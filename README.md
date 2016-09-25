# mirrors-cn-protocol

## 简介
mirrors-cn.com 是一个利用DNS智能解析以实现国内软件源的智能选择功能的项目。例如对于Archlinux的镜像，用户可以通过统一的 http[s]://archlinux.mirrors-cn.com/archlinux 来访问。archlinux.mirrors-cn.com会智能解析到离用户最近的站点，从而实现速度上的提升。

## 协议
为了所有解析到的具体镜像站都能提供相同的服务，一个统一彼此表现的协议是必要的。本协议目前包括以下内容：

- 标准URL
- 标准行为

### 重定向源与非重定向源
下文中的“重定向源”，指称经过0次或若干次HTTP 301/302重定向，最终能够返回目标文件的镜像源。重定向源的实现较为简单，但部分客户端可能不支持重定向功能。

下文中的“非重定向源”，指称不经过HTTP重定向，能够直接返回目标文件的镜像源。一般情况下，非重定向源会持有域名证书私钥以响应HTTPS请求。

### 概述
所有加入mirrors-cn.com某一镜像服务的站点，都应能：
- 同时响应HTTP与HTTPS协议GET Host = mirror_name.mirrors-cn.com 请求，并在请求对象合法的前提下，若干次301/302重定向后，返回相同的内容。

### /
对于GET mirror_name.mirrors-cn.com/ 的请求，服务器应返回200 OK与合法HTML页面。其中应包括：
- mirrors-cn.com的备案信息
- https://github.com/sjtug/mirrors-cn-protocol 的链接

### ArchLinux

| Key | Value |
|:---:|:-----:|
|重定向源 | archlinux.mirrors-cn.com/archlinux |
| 非重定向源 | archlinux-noredir.mirrors-cn.com/archlinux |
| 说明 | 同步间隔不应长于3小时，满足[https://wiki.archlinux.org/index.php/DeveloperWiki:NewMirrors](官方)对Tier2 Mirror的要求 | 

#### 当前站点
##### 重定向源
- ...
- ...

##### 非重定向源
- ...

