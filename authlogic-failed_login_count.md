---
title: authlogic failed_login_count 
date: 2019-05-27
---

Magic Columns `failed_login_count` 有点类似 rails的 `created_at` `updated_at`

选项 `consecutive_failed_logins_limit`

默认是 50 

![](https://cos.ap-beijing.myqcloud.com/data-1252438752/1558932316.png)

reset 机制

`session/base.rb` 的验证

```
      validate :reset_failed_login_count, if: :reset_failed_login_count?
```

![](https://cos.ap-beijing.myqcloud.com/data-1252438752/1558932944.png)

`exceeded_failed_logins_limit?` 是否超过了最大登录限制

`being_brute_force_protected?` 这个method可以看到默认是2个小时

![](https://cos.ap-beijing.myqcloud.com/data-1252438752/1558933485.png)

![](https://cos.ap-beijing.myqcloud.com/data-1252438752/1558933140.png)

https://github.com/binarylogic/authlogic/blob/b204c8dcc01f0047386a7a8cefa671a05c50f6c1/lib/authlogic/session/base.rb#L591-L599