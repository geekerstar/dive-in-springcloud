## 微服务
微服务是一种架构风格

- 一系列微小的服务共同组成
- 跑在自己的进程里
- 每个服务为独立的业务开发
- 独立部署
- 分布式的管理

![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/1.jpg)

## 点餐系统
设计的架构形态
- 单体架构
- 基于Ajax的前后端分离
- 分布式（水平扩展 & 服务拆分）

## 单体架构
![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/2.png)

### 单体架构优点
- 容易测试
- 容易部署

### 单体架构缺点
- 开发效率低
- 代码维护难
- 部署不灵活
- 稳定性不高
- 扩展性不够

### 基于Ajax的前后端分离
![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/3.png)

### 点餐服务的前后端分离
![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/4.png)

## 分布式定义

旨在支持应用程序和服务的开发，可以利用物理架构由多个自治的处理元素，不共享主内存，但通过网络发送消息合作

## 简单的微服务架构

![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/5.jpg)

## 微服务架构的基础框架/组件

- 服务注册发现
- 服务网关（Service Gateway）
- 后端通用服务（也称中间层服务Middle Tier Service）
- 前端服务（也称边缘服务Edge Service)

## SpringCloud Eureka
基于Netflix Eureka做了二次封装

![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/7.png)


两个组件

 - Eureka Server 注册中心
 - Eureka Client 服务注册

## Eureka Server 高可用
![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/6.png)

## Eureka总结
- @EnableEurekaServer
- @EnableEurekaClient
- 心跳检测、健康检查、负载均衡等功能
- Eureka高可用，生产上建议至少两台以上
- 分布式系统中，服务注册中心是最重要的基础部分

## 分布式系统中为什么需要服务发现？

![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/8.png)


## 服务发现的两种方式
- 客户端发现（Eureka)
- 服务端发现（Nginx、Zookeeper、Kubernetes）


### 微服务的特点：异构

- 不同语言
- 不同类型的数据库

### Springcloud的服务调用方式
- REST
- Node.js的eureka-js-client
