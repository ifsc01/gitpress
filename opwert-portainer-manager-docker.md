---
title:  openwrt 配置 Portainer 管理 docker记录
date: 2019-04-27
---

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

![](https://cos.ap-beijing.myqcloud.com/data-1252438752/1558937322.png)

