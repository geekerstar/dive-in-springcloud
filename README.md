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

### 分布式定义

旨在支持应用程序和服务的开发，可以利用物理架构由多个自治的处理元素，不共享主内存，但通过网络发送消息合作

### 简单的微服务架构

![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/5.jpg)

### 微服务架构的基础框架/组件

- 服务注册发现
- 服务网关（Service Gateway）
- 后端通用服务（也称中间层服务Middle Tier Service）
- 前端服务（也称边缘服务Edge Service)

### SpringCloud Eureka
基于Netflix Eureka做了二次封装

![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/7.png)


两个组件

 - Eureka Server 注册中心
 - Eureka Client 服务注册

### Eureka Server 高可用
![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/6.png)

### Eureka总结
- @EnableEurekaServer
- @EnableEurekaClient
- 心跳检测、健康检查、负载均衡等功能
- Eureka高可用，生产上建议至少两台以上
- 分布式系统中，服务注册中心是最重要的基础部分

## 分布式系统中为什么需要服务发现？

![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/8.png)


### 服务发现的两种方式
- 客户端发现（Eureka)
- 服务端发现（Nginx、Zookeeper、Kubernetes）


### 微服务的特点：异构

- 不同语言
- 不同类型的数据库

### Springcloud的服务调用方式
- REST
- Node.js的eureka-js-client

## 服务拆分 - 起点和终点？
起点：

- 既有架构的形态

终点：

- 好的架构不是设计出来的，而是进化而来的
- 一直在演进

### 适合上微服务吗？
业务形态不适合的
- 系统中包含很多强事务场景的
- 业务相对稳定，迭代周期长
- 访问压力不大，可用性要求不高

### 康威定律
任何组织在设计一套系统（广义概念上的系统）时，所交付的设计方案在结构上都与该组织的沟通结构保持一致

### 微服务和团队结构
微服务的特点
- 一系列微小的服务共同组成
- 单独部署，跑在自己的进程里
- 每个服务为独立的业务开发
- 分布式的管理

![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/9.jpg)

### 服务拆分的方法论
扩展立方模型（Scale Cube)
- X轴 水平复制
- Z轴 数据区分
- Y轴 功能解耦

![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/10.png)

如何拆"功能"？
- 单一职责，松耦合，高内聚
- 关注分离点（按职责、通用性、粒度级别）

服务和数据的关系：
- 先考虑业务功能，再考虑数据
- 无状态服务

如何拆"数据"？
- 每个微服务都有单独的数据存储
- 依据服务特点选择不同结构的数据库类型
- 难点在确定边界（针对边界设计API、依据边界权衡数据冗余）

![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/11.png)

### 点餐业务服务拆分分析

![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/12.png)

## 应用间通信
Springcloud中服务间两种RESTFul调用方式

- RestTemplate

- Feign

### RestTemplate

订单服务 -> 商品服务

### 客户端负载均衡 - Ribbon

- RestTemplate

- Feign

- Zuul

#### 特点

- 服务发现

- 服务选择规则

- 服务监听

#### 主要组件

- ServerList

- IRule

- ServerListFilter

### Feign

- 声明式REST客户端（伪RPC）

- 采用了基于接口的注解

### 多模块划分

- product-server：所有业务逻辑

- product-client：对外暴露的接口

- product-common：公用的对象

#### 依赖关系

![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/13.png)


### 同步 or 异步

![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/14.png)

### 微服务和容器 - 天生一对

- 从系统环境开始，自底至上打包应用
- 轻量级，对资源的有效隔离和管理
- 可复用，版本化

![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/15.png)

## 统一配置中心
为什么需要统一配置中心？

- 不方便维护
- 配置内容安全与权限
- 更新配置项目需要重启

![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/16.png)

## 异步
客户端请求不会阻塞进程，服务端的响应可以是非即时的

### 异步的常见形态
- 通知
- 请求/异步响应
- 消息

### MQ使用场景
- 异步处理
- 流量削峰
- 日志处理
- 应用解耦

## Spring cloud Stream

![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/17.png)

## 原始流程
- 1、查询商品信息（调用商品服务）
- 2、计算总价（生成订单详情）
- 3、商品服务扣库存（调用商品服务）
- 4、订单入库（生成订单）

### 异步扣库存分析
![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/18.png)
![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/19.png)

- 可靠的消息投递
- 用户体验的变化

### 具体操作

- 1、库存在Redis中保存
- 2、收到请求Redis判断是否库存充足，减掉Redis中库存
- 3、订单服务创建订单写入数据库，并发送消息

## 异步和消息处理
- 数据一致性
- Dubbo+Zookeeper和Springcloud

## 服务网关
### 为什么需要服务网关
![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/20.png)

### 服务网关的要素
- 稳定性和高可用
- 性能和并发性
- 安全性
- 扩展性

### 常用的网关方案
- Nginx+Lua
- Kong
- Tyk
- Springcloud Zuul

### Zuul的特点
- 路由+过滤器=Zuul
- 核心是一系列的过滤器

### Zuul的四种过滤器API
- 前置（Pre)：限流、鉴权、参数校验调整
- 后置（Post）：统计、日志
- 路由（Route）
- 错误（Error）

![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/21.jpg)

### 请求生命周期
![](https://github.com/geekerstar/dive-in-springcloud/blob/master/img/22.jpg)

### Zuul的高可用
- 多个Zuul节点注册到Eureka Server
- Nginx和Zuul"混搭"
