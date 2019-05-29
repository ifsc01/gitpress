---
title:  体验下 minikube 
date: 2019-05-28
---

* docs: https://github.com/kubernetes/minikube#installation 
* https://kubernetes.io/docs/tasks/tools/install-minikube/
* 平台: macos

VMware Fusion 作为虚拟机管理程序


## 安装 `kubectl`
https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-on-macos

命令行工具 `kubectl` 可以对Kubernetes集群进行操作

brew 安装

```bash
brew install kubernetes-cli
```

## 安装 minikube

```bash
brew cask install minikube
```

启动 minikube 创建集群

```bash
minikube start
```

使用 vmwarefusion 

```bash
minikube --vm-driver=vmwarefusion --loglevel 2 start
```

默认是 virtualbox

```
--vm-driver string                VM driver is one of: [virtualbox xhyve vmwarefusion] (default "virtualbox")
```


## 部署 echoserver 

部署 一个简单的http server `echoserver` 

![](https://data-1252438752.cos.ap-beijing.myqcloud.com/2019/05/30/15591583695942.jpg)

```bash
$ kubectl run hello-minikube --image=k8s.gcr.io/echoserver:1.10 --port=8080
deployment.apps/hello-minikube created
```

要访问hello-minikue, 发布服务

选项`--type=NodePort`指定服务的类型

```bash
kubectl expose deployment hello-minikube --type=NodePort
```

![](https://data-1252438752.cos.ap-beijing.myqcloud.com/2019/05/30/15591583561654.jpg)

hello-minikube Pod现已启动，但必须等到Pod启动才能通过公开的服务访问它
查看状态 `kubectl get pod`

![](https://data-1252438752.cos.ap-beijing.myqcloud.com/2019/05/30/15591585372597.jpg)

获取公开的服务的URL以查看服务详细信息：

![](https://data-1252438752.cos.ap-beijing.myqcloud.com/2019/05/30/15591603987233.jpg)

地址 http://172.16.105.133:32374

![](https://data-1252438752.cos.ap-beijing.myqcloud.com/2019/05/30/15591586399602.jpg)


## 测试nginx

![](https://data-1252438752.cos.ap-beijing.myqcloud.com/2019/05/30/15591602934977.jpg)

 可以访问了
 
![](https://data-1252438752.cos.ap-beijing.myqcloud.com/2019/05/30/15591602279657.jpg)



