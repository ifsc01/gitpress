---
title:  openwrt LEDE 记录
date: 2019-05-26
---

把一台x86的闲置台式机安装了lede路由系统做软路由

终于把去年买好的网卡用上了!!!

![](https://cos.ap-beijing.myqcloud.com/dropshare-1252438752/1559063834.png)


![](https://cos.ap-beijing.myqcloud.com/dropshare-1252438752/1559063771.jpg)

## openwrt 安装记录

下载地址 

http://firmware.koolshare.cn/LEDE_X64_fw867/

![telegram-cloud-photo-size-5-6292077946080438431-x](https://cos.ap-beijing.myqcloud.com/dropshare-1252438752/1558985503.png)
combined和 uefi-gpt 两种，前者支持MBR的分区表和BIOS系统，后者支持GPT 分区表和EFI系统

我用的 combined 的 固件

mac或者linux直接用dd写入磁盘就行

下载解压

使用dd 写到硬盘

```
sudo dd if=./openwrt-koolshare-mod-v2.31-r10822-50aa0525d1-x86-64-combined-squashfs.img   of=/dev/disk2
```

## 配置网络tips

外网不能访问, 需要配置下防火墙

![](https://cos.ap-beijing.myqcloud.com/dropshare-1252438752/1559063483.png)
 

## openwrt 配置 Portainer 管理 docker记录

Portainer 概述
* [GitHub] https://github.com/portainer/portainer
* [Doc] https://portainer.readthedocs.io/en/stable/


使用的路由器系统是LEDE

在酷软里安装docker

![](https://cos.ap-beijing.myqcloud.com/data-1252438752/1558935109.png)

配置

![](https://cos.ap-beijing.myqcloud.com/data-1252438752/1558934523.png)

![](https://cos.ap-beijing.myqcloud.com/data-1252438752/1558934545.png)

这个插件的容器管理有问题, 直接 ssh或者使用 Shellinabox 

![](https://cos.ap-beijing.myqcloud.com/data-1252438752/1558936751.png)

```
 docker run -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/mnt/sda3/portainer_data portainer/portainer
 ```

 `/mnt/sda3/portainer_data` 是数据目录

容器已经跑起来了

```
root@Openwrt:/mnt/sda3# docker ps
CONTAINER ID        IMAGE                 COMMAND             CREATED             STATUS              PORTS                    NAMES
f3d7ef5f222b        portainer/portainer   "/portainer"        5 seconds ago       Up 4 seconds        0.0.0.0:9000->9000/tcp   epic_shaw
```

可以进入portainer配置了

选择对 宿主机的docker进行管理

![](https://cos.ap-beijing.myqcloud.com/data-1252438752/1558937080.png)


Portainer  界面

![](https://cos.ap-beijing.myqcloud.com/data-1252438752/1558937322.png)

