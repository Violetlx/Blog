---
title: SpringCloud微服务项目
tags:
  - - 程序员
categories:
  - - 程序员
description: SpringCloud微服务项目
top_img: >-
  https://img.bjsxt.com/uploadfile/2018/08/Spring-Cloud-2.jpg
cover: >-
  https://img.bjsxt.com/uploadfile/2018/08/Spring-Cloud-2.jpg
abbrlink: 6ed5eebe
date: 2024-09-23 16:01:27
---

# 技术



## 1.前端项目

- 采用 **Vue3 + TS + ElementPlus**



## 2.后端项目结构

- 采用插件化 + 扩展包形式 结构解耦 已于扩展



## 3.后端代码风格

- 严格遵守 **Alibaba** 规范与项目统一配置的代码格式化



## 4.分布式注册中心

- **Alibaba Nacos**



## 5.分布式配置中心

- **Alibaba Nacos**



## 6.服务网关

- **SpringCloud Gateway**



## 7.负载均衡

- **SpringCloud Loadbalancer**



## 8.RPC 远程调用

- **Apache Dubbo 3.x**
- **OpenFeign**



## 9.分布式限流熔断

- **Alibaba Sentinel**



## 10.分布式事务

- **Alibaba Seata**



## 11.Web 容器

- 采用 **Undertow** 基于 **XNIO** 的高性能容器



## 12.权限认证

- **Sa-Token**
- **Spring Security**



## 13.权限注解

- **Sa-Token**
- **Spring Security**



## 14.关系型数据库

- **MySQL**
- **Oracle**
- **PostgreSQL**
- **SQLServer**
- 使用异构切换（支持 **mybatis-plus** 支持的所有数据库）

## 15.缓存数据库

- **Redis**



## 16.Redis客户端

- **Redisson**



## 17.缓存注解

- **Spring-Cache**



## 18.ORM 框架

- **Mybatis-Plus**



## 19.SQL 监控

- **p6spy**



## 20.数据分页

- **Mybatis-Plus** 分页插件



## 21.数据权限

- 采用 **Mybatis-Plus** 插件，自行分析拼接 **SQL** 无感式过滤，只需要为 **Mapper** 设置好注解条件 支持多种自定义 不限于部门角色



## 22.数据脱敏

- 注解 + **jackson**



## 23.多数据源框架

- **dynamic-datasource**



## 24.多数据源事务

- **dynamic-datasource**



## 25.数据库连接池

- **HikariCP**



## 26.数据库主键

- 采用 **雪花ID 基于时间戳的 有序增长 唯一ID** 



## 27.WebSocket协议

- 基于 Spring 封装的 WebSocket 协议，扩展 Token 鉴权与分布式会话，不局限于单机



## 28.SSE 推送

- **Spring SSE**



## 29.序列化

- **Jackson**



## 30.分布式幂等

- 美团 **GTIS**



## 31.分布式任务调度

- **SnailJob**
- **XxlJob**



## 32.分布式日志中心

- **ELK**



## 33.分布式搜索引擎

- 采用 ElasticSearch 、Easy-Es 以 Mybatis-Plus 方式操作 ElasticSearch



## 34.分布式消息队列

- **Kafaka**
- **RockketMQ**
- **RabbitMQ**



## 35.分布式消息总线

- 采用 SpringCloud Bus 实现事件总线 跨服务通知，支持 Kafaka 、RocketMQ 、RabbitM!Q



## 36.分库分表功能

- **Apache Sharding-Proxy**



## 37.文件存储

- 采用 **Minio** 分布式文件存储 支持 七牛、阿里、腾讯 等一切支持 **S3** 协议的厂家



## 38.短信

- **sms**



## 39.邮件

- **mail-api**



## 40.接口文档

- **SpringDoc javadoc**
- **swagger2 knife4j**



## 41.校验框架

- **Validation**



## 42.Excel 框架

- **Alibaba EasyExcel**



## 43.工作流支持

- **Flowable**
- **activiti**



## 44.工具类框架

- **Hutool**
- **Lombok**



## 45.服务监控框架

- **Spring-Admin**



## 46.全方位监控报警

- **Prometheus  Grafana**



## 47.链路追踪

- **Apache SkyWalking**



## 48.代码生成器

- 只需设计好表结构 一键生成所有 CRUD 代码页面
- 降低 80% 的开发量，把精力投入业务涉及上
- 框架为其适配 MP、SpringDoc 规范化代码，同时支持动态多数据源代码生成



## 49.部署方式

- **Docker**



## 50.国际化

