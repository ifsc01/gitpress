---
title: LEDE 软路由安装
date: 2019-05-25
---

下载地址 

http://firmware.koolshare.cn/LEDE_X64_fw867/

![telegram-cloud-photo-size-5-6292077946080438431-x](https://cos.ap-beijing.myqcloud.com/dropshare-1252438752/1558985503.png)


combined和 uefi-gpt 两种，前者支持MBR的分区表和BIOS系统，后者支持GPT 分区表和EFI系统


mac或者linux直接用dd写入磁盘就行

下载解压

```
sudo dd if=./openwrt-koolshare-mod-v2.31-r10822-50aa0525d1-x86-64-combined-squashfs.img   of=/dev/disk2
```
 