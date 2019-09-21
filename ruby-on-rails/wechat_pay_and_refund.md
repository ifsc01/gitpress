---
title: 微信支付退款接入小记
date: 2019-09-22
---

## 支付

GEM: https://github.com/jasl/wx_pay

## 沙箱模式

不建议用,各种问题

## 退款

请求微信退款

```ruby
result = WxPay::Service.invoke_refund(refund_params)
```

refund_params 需要 notify_url 在真正退款成功时, 通知服务器

```ruby
    refund_params = {
      out_refund_no: refund_order.refund_no,
      total_fee: (pay_fee * 100).to_i,
      refund_fee: (pay_fee * 100).to_i,
      transaction_id: wx_transaction_id,
      notify_url: Order.wx_refund_notify_url
    }
```

处理退款回调

```ruby

  def refund_notify
    result = Hash.from_xml(request.body.read)["xml"]

    if result['return_code'] == 'SUCCESS'
      req_info = result['req_info']
      decrypt_result = Refund.decrypt_refund_info(req_info)
      refund = Refund.find_by refund_no: decrypt_result['out_refund_no']
      if refund
        refund.update(status: :success, refund_info: decrypt_result)
      end
      render :xml => {return_code: "SUCCESS"}.to_xml(root: 'xml', dasherize: false)
    else
      render :xml => {return_code: "FAIL", return_msg: "签名失败"}.to_xml(root: 'xml', dasherize: false)
    end
  end
```

`result['req_info']` 是加密的, 需要解密

`decrypt_refund_info` 

```ruby

class Refund < ApplicationRecord
  belongs_to :order
  belongs_to :user

  enum status: { wait_refund: 0, request: 1, success: 2, fail: 3 }, _suffix: true


  def self.decrypt_refund_info(req_info)
    str = Base64.decode64(req_info) #先对结果进行base64解码
    aes_data = self.aes_ecb_decrypt(str) #得到xml字符串
    Hash.from_xml(aes_data)['root']
  end

  def self.aes_ecb_decrypt(req_info)
    aes = OpenSSL::Cipher::AES.new("256-ECB")
    aes.decrypt
    aes.key = md5_pay_key
    aes.update(req_info) + aes.final
  end

  def self.md5_pay_key
    Digest::MD5.hexdigest(WxPay.key)
  end

  before_create :set_refund_no
  def set_refund_no
    self.refund_no = 'r'+generate_refund_no
  end

  def generate_refund_no
    loop do
      number = format('%05d',SecureRandom.random_number(99999))
      no = Time.zone.now.to_formatted_s(:number).to_s + number
      break no unless Refund.where(refund_no: no).exists?
    end
  end
end
```