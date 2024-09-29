---
title: Nacos 安装与使用
tags:
  - - nacos
categories:
  - - 环境搭建
description: Nacos 安装与使用
top_img: >-
  https://cdn.apifox.cn/app/project-icon/custom/20221110/b67baa75-a01e-49c3-81fc-da1f2982343a.jpeg
cover: >-
  https://cdn.apifox.cn/app/project-icon/custom/20221110/b67baa75-a01e-49c3-81fc-da1f2982343a.jpeg
abbrlink: 95afb97c
date: 2024-09-24 17:00:26
---

![ https://pic2.zhimg.com/v2-71daae9a4aef25ce7a01606571b2365a_r.jpg](https://pic2.zhimg.com/v2-71daae9a4aef25ce7a01606571b2365a_r.jpg)



# 概述



## 服务注册与发现

微服务与传统单体式应用架构最大区别就是强调软件模块的拆分。在单体架构下，一个应用系统的多个功能模块由于组织在一起在同一个应用进程内部署与运行，因此，模块之间直接通过方法调用即可完成对一次请求得响应。但在微服务系统中需要对一个应用系统根据其功能特点，按照一定粒度进行拆分后单独部署，以便实现模块内的高内聚，模块间的低耦合，实现整个微服务系统的高可扩展性。原来一次在一个应用内即可完成的请求处理，会出现跨进程跨主机的微服务调用，如何让这个服务之间能够互相发现像单体式应用一样提供统一对外的服务调用能力式微服务框架层面需要重点解决的核心问题之一。

在 Spring Cloud 生态中，采用了如下服务注册与发现模型，来实现微服务之间的相互发现与调用。

![服务注册与发现模型](https://sca.aliyun.com/img/user/quickstart/nacos/service-discovery.png)

如上图所示，通过在微服务系统中引入一个叫做注册中心的组件，来作为协调者。其最简化的过程是，所有的微服务应用在启动过程中会将自身包含服务名称、主机 IP 地址和端口号等信息发送到注册中心中，然后上游的微服务在处理请求过程中，根据服务名称到注册中心查找对应服务的所有实例 IP 地址和端口号来进行服务调用，整个过程中如图中虚线所示。从而让分散的微服务系统之间能够像一个整体一样对外提供请求处理能力。



## 配置管理

在正式介绍分布式配置内容之前，还是先简单介绍一下配置的概念。

软件系统中的配置是指在软件运行过程中所需要的各种设定和参数，包括系统配置、应用配置和用户配置等。

- 系统配置包括操作系统、硬件和网络等基本环境参数的设定
- 应用配置包括应用程序的各种参数和选项的设定，如数据库连接字符串、日志级别等
- 用户配置则是指用户自定义的各种选项和参数，如快捷键、界面布局、语言等

配置在软件系统中是对软件源代码的一种重要补充，通过其可以便捷的调整软件系统的执行行为，让软件系统更加灵活。

除了单体应用，在分布式系统中，配置信息应用非常广泛，可以通过配置来实现不同的功能。这些配置信息如数据库连接信息、日志级别、业务配置等等。

在传统的开发中，这些配置西南西通常硬编码到应用程序的代码中，与程序代码一起打包和部署。然而，这种方式有很多缺点，比如配置不易维护，只要修改配置就得重新构建和部署等。

![service-config](https://sca.aliyun.com/img/user/quickstart/nacos/spring-cloud-config.png)

采用分布式配置中心的软件架构如上图所示，其可以在分布式场景中帮助解决以下问题：

1. 管理应用程序配置：当有大量应用程序需要管理时，手动维护配置文件会变得非常困难。分布式配置中心提供了一个集中管理和分发配置信息的解决方案。
2. 环境隔离：在开发、测试和生产等不同环境中，应用程序的配置信息往往都会有不同。使用分布式配置中心，可以轻松管理和分发不同环境下的配置信息。
3. 提高程序安全性：将配置信息存储在代码库或应用程序文件中可能会导致安全风险，因为这些信息可能会被意外地泄露或被恶意攻击者利用。使用分布式配置，可以将配置信息加密和保护，并且可以进行访问权限控制。
4. 动态更新配置：在应用程序运行时，可能需要动态地更新配置信息，以便应用程序可以及时响应变化。使用分布式配置中心，可以在运行时动态更新配置信息，而无需重新启动应用程序。



## Nacos 概述

[Nacos](https://nacos.io/zh-cn/) /nɑ:k əʊs/ 是 Dynamic Naming and Configuration Service 的首字母简称，一个更易于构建云原生应用的动态服务发现、配置管理和服务管理平台。

Nacos 致力于帮助发现、配置和管理微服务。Nacos 提供了一组简单易用的特性集，帮助你快速实现动态服务发现、服务配置、服务元数据及流量管理。

Nacos 可以更敏捷和更容易地构建、交付和管理微服务平台。Nacos 是构建以 **服务** 为中心的现代应用架构（例如微服务范式、云原生范式）的服务基础设施。



------



# 快速开始

使用 `spring-cloud-starter-alibaba-nacos-config` 和 `spring-cloud-starter-alibaba-nacos-discovery` 完成 Spring Cloud 应用的配置管理和服务发现。



## 安装 Nacos Server

### 接入云上免费版本

体验 Spring Cloud Alibaba 注册配置中心的最简单方式就是接入阿里云上的托管 Nacos Server ，这样可以免去本地安装下载的繁琐步骤。具体参考 [如何体验和接入阿里云托管免费 Nacos Server](https://free.aliyun.com/?searchKey=nacos&spm=sca-quickstart-free.topbar.0.0.0)。

> 如果是用的云上托管版本 Nacos Server ，在接下来的文档使用 云上 `Nacos Server` 地址 替换 `127.0.0.1:8848` 即可。
>

### 本地安装方式

具体启动方式参考 [Nacos](https://nacos.io/zh-cn/docs/quick-start.html) 官网。

Nacos Server 启动成功之后，浏览器地址栏输入 `http://ip:8848/nacos` 查看 Nacos 控制台（默认账号名称和密码为 nacos/nacos）：

![nacos-server-start](https://sca.aliyun.com/img/user/quickstart/nacos/nacos-config-dashboard.png)

关于更多的 Nacos Server 版本，可以从 Nacos 官方 [release](https://github.com/alibaba/nacos/releases) 页面查看。



## 接入 Nacos 配置中心

### 接入 Nacos Config

如果在你的项目中使用 Nacos 来实现配置管理，需要进行以下操作（确保 Nacos Server 已启动）：

1. 需要在 pom.xml 文件中引入 group ID 为 com.alibaba.cloud 和 atrfact ID 为 spring-cloud-starter-alibaba-nacos-config 的 starter:

   ```xml
   <dependency>
       <groupId>com.alibaba.cloud</groupId>
       <artifactId>spring-cloud-starter-alibaba-nacos-config</artifactId>
   </dependency>
   ```

2. 在应用的 /src/main/resources/application.yaml 配置文件中配置 Nacos Config 地址并引入服务配置：

   ```yaml
   spring:
     cloud:
       nacos:
         serverAddr: 127.0.0.1:8848 #如果用的云上托管版本，输入可访问的Nacos Server地址即可
     config:
       import:
         - nacos:nacos-config-example.properties?refreshEnabled=true
   ```

3. 完成上述两步后，应用会从 Nacos Server 中获取相应的配置，并添加在 Spring Environment 的 PropertySources 中。假设我们通过 Nacos 作为配置中心保存应用服务的部分配置，有以下几种方式实现：

   - BeanAutoRefreshConfigExample：通过将配置信息配置给 bean ，支持配置变自动刷新；
   - ConfigListenerExample：监听配置信息；
   - DockingInterfaceExample：对接 Nacos 接口，通过接口完成对配置信息增删改查；
   - ValueAnnotationExample：通过 @Value 注解进行配置信息获取。



### 添加 Nacos 配置

1. 命令方式：

   ```sh
   $ curl -X POST "http://127.0.0.1:8848/nacos/v1/cs/configs?dataId=nacos-config-example.properties&group=DEFAULT_GROUP&content=spring.cloud.nacos.config.serverAddr=127.0.0.1:8848%0Aspring.cloud.nacos.config.prefix=PREFIX%0Aspring.cloud.nacos.config.group=GROUP%0Aspring.cloud.nacos.config.namespace=NAMESPACE"
   ```

2. 控制台方式（推荐使用）

   ```properties
   dataId 为：nacos-config-example.properties
   group 为：DEFAULT_GROUP
   ```

   配置内容如下：

   ```properties
   spring.cloud.nacos.config.serveraddr=127.0.0.1:8848
   spring.cloud.nacos.config.prefix=PREFIX
   spring.cloud.nacos.config.group=GROUP
   spring.cloud.nacos.config.namespace=NAMESPACE
   ```



### 启动应用并验证

**应用启动**

1. 添加其他配置：在应用的 src/main/resources/application.yaml 中添加基本配置信息：

   ```yaml
   server:
     port: 18084
   management:
     endpoints:
       web:
         exposure:
           include: "*"
   ```

2. 启动应用，支持 IDE 直接启动和编译打包后启动。

   - IDE 直接启动：找到主类 NacosConfigApplication ，执行 main 方法启动应用。
   - 打包编译后启动：首先执行 mvn clean package 将工程编译打包，然后执行 java-jar nacos-config-example.jar 启动应用。



**功能验证**

1. 验证自动注入

   请求 http://127.0.0.1:18084/nacos/bean 地址，可以看到成功从 Nacos 配置中心中获取了数据。

   ```sh
   $ curl http://127.0.0.1:18084/nacos/bean
   ```

   响应结果：

   ```json
   {
   
     "serverAddr": "127.0.0.1:8848",
   
     "prefix": "PREFIX",
   
     "namespace": "NAMESPACE",
   
     "group": "GROUP"
   
   }
   ```

2. 验证动态刷新

   在命令行终端执行以下命令刷新 Nacos 的配置信息：

   ```sh
   $ curl -X POST "http://127.0.0.1:8848/nacos/v1/cs/configs?dataId=nacos-config-example.properties&group=DEFAULT_GROUP&content=spring.cloud.nacos.config.serveraddr=127.0.0.1:8848%0Aspring.cloud.nacos.config.prefix=PREFIX%0Aspring.cloud.nacos.config.group=DEFAULT_GROUP%0Aspring.cloud.nacos.config.namespace=NAMESPACE"
   ```

   再次请求 http://127.0.0.1:18084/nacos/bean 地址，可以看到应用已经从 Nacos 中获取到了最新的数据。

   ```sh
   $ curl http://127.0.0.1:18084/nacos/bean
   ```

   响应结果：

   ```json
   {
     "serverAddr": "127.0.0.1:8848",
     "prefix": "PREFIX",
     "namespace": "NAMESPACE",
     "group": "DEFAULT_GROUP"
   }
   ```

   Nacos 配置管理示例源码参考：[Nacos 配置管理示例](https://github.com/alibaba/spring-cloud-alibaba/tree/2022.x/spring-cloud-alibaba-examples/nacos-example/nacos-config-example)



## 接入 Nacos 服务注册与发现

### 接入 Nacos Discovery

如果要在你的项目中使用 Nacos 来作为服务发现的组件。需要进行以下操作（确保 Nacos Server 已启动）：

1. 需要在 pom.xml 文件中引入 group ID 为 com.alibaba.cloud 和 artifact ID 为 spring-cloud-stater-alibaba-nacos-discovery 的 stater：

   ```xml
   <dependency>
       <groupId>com.alibaba.cloud</groupId>
       <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
   </dependency>
   ```

2. 添加应用配置：在应用的 /src/main/resources/application.properties 配置文件中配置 Nacos Server 地址：

   ```properties
   spring.cloud.nacos.discovery.server-addr=127.0.0.1:8848
   ```

3. 使用 @EnableDiscoveryClient 注解开启服务注册与发现功能：

   ```java
   @SpringBootApplication
   @EnableDiscoveryClient
   public class ProviderApplication {
   
       public static void main(String[] args) {
           SpringApplication.run(ProviderApplication.class, args);
       }
   
       @RestController
       class EchoController {
           @GetMapping(value = "/echo/{string}")
           public String echo(@PathVariable String string) {
               return string;
           }
       }
   }
   ```



### 启动应用并验证

**应用启动**

1. 添加配置：在 [nacos-discovery-provider-example](https://github.com/alibaba/spring-cloud-alibaba/tree/2022.x/spring-cloud-alibaba-examples/nacos-example/nacos-discovery-example/nacos-discovery-provider-example) 项目的 /src/main/resources/application.properties 中添加基本配置信息:

   ```
   spring.application.name=service-provider
   
   server.port=18082
   ```

2. 启动应用，支持 IDE 直接启动和编译打包后启动。

   - IDE 直接启动：找到 [nacos-discovery-provider-example](https://github.com/alibaba/spring-cloud-alibaba/tree/2022.x/spring-cloud-alibaba-examples/nacos-example/nacos-discovery-example/nacos-discovery-provider-example) 项目的主类 ProviderApplication，执行 main 方法启动应用。
   - 打包编译后启动：在 [nacos-discovery-provider-example](https://github.com/alibaba/spring-cloud-alibaba/tree/2022.x/spring-cloud-alibaba-examples/nacos-example/nacos-discovery-example/nacos-discovery-provider-example) 项目中执行 mvn clean package 将工程编译打包，然后执行 java - jar nacos-discovery-provider-example.jar 启动应用。

**验证**

1. 查询服务

   使用 Shell 终端输入如下命令查询，可以看到服务节点已经成功注册到 Nacos Server。

   Terminal window

   ```sh
   $ curl http://127.0.0.1:8848/nacos/v1/ns/catalog/instances?serviceName=service-provider&clusterName=DEFAULT&pageSize=10&pageNo=1&namespaceId=
   ```

   响应结果：

   ```json
   {
   
     "list": [
   
       {
   
         "ip": "192.168.3.19",
   
         "port": 1000,
   
         "weight": 1,
   
         "healthy": true,
   
         "enabled": true,
   
         "ephemeral": true,
   
         "clusterName": "DEFAULT",
   
         "serviceName": "DEFAULT_GROUP@@service-provider",
   
         "metadata": {
   
           "preserved.register.source": "SPRING_CLOUD"
   
         },
   
         "instanceHeartBeatInterval": 5000,
   
         "instanceHeartBeatTimeOut": 15000,
   
         "ipDeleteTimeout": 30000
   
       }
   
     ],
   
     "count": 1
   
   }
   ```

2. 服务发现

   在 pom.xml 中加入以下依赖：

   ```xml
   <dependencies>
   
       <dependency>
   
           <groupId>org.springframework.cloud</groupId>
   
           <artifactId>spring-cloud-loadbalancer</artifactId>
   
       </dependency>
   
   </dependencies>
   ```

   在配置文件中加入以下配置：

   ```properties
   spring.cloud.loadbalancer.ribbon.enabled=false
   
   spring.cloud.loadbalancer.nacos.enabled=true
   ```



### 服务消费

#### 应用配置

本章节只是为了便于您理解接入方式，此处只涉及 Ribbon、RestTemplate、FeignClient 相关内容，如果已经使用了其他服务发现组件，可以通过直接替换依赖来接入 spring-cloud-starter-alibaba-nacos-config。

1. 添加 @LoadBlanced 注解，使得 RestTemplate 接入 Ribbon：

   ```java
   @Bean
   @LoadBalanced
   public RestTemplate restTemplate() {
       return new RestTemplate();
   }
   ```

2. FeignClient 已经默认集成了 Ribbon ，此处演示如何配置一个 FeignClient：

   ```java
   @FeignClient(name = "service-provider")
   public interface EchoService {
       @GetMapping(value = "/echo/{str}")
       String echo(@PathVariable("str") String str);
   }
   ```

   使用 @FeignClient 注解将 EchoService 这个接口包装成一个 FeignClient，属性 name 对应服务名 service-provider。

   echo 方法上的 @GetMapping 注解将 echo 方法与 URL “/echo/{str}” 相对应，@PathVariable 注解将 URL 路径中的 {str} 对应成 echo 方法的参数 str。

3. 将两者注入到 Controller 中：

   ```java
   @RestController 
   public class TestController {
       @Autowired    
       private RestTemplate restTemplate;    
       @Autowired    
       private EchoService echoService;
       
       @GetMapping(value = "/echo-rest/{str}")    
       public String rest(@PathVariable String str) {        
           return restTemplate.getForObject("http://service-provider/echo/" + str, String.class);    
       }    
       
       @GetMapping(value = "/echo-feign/{str}")    
       public String feign(@PathVariable String str) {        
           return echoService.echo(str);    
       }
   }
   ```

4. 添加必要的配置：

   在 [nacos-discovery-consumer-example](https://github.com/alibaba/spring-cloud-alibaba/tree/2022.x/spring-cloud-alibaba-examples/nacos-example/nacos-discovery-example/nacos-discovery-consumer-example) 项目的 /src/main/resources/application.properties 中添加基本配置信息：

   ```properties
   spring.application.name=service-consumer
   
   server.port=18083
   ```

5. 启动应用

   - IDE 直接启动：找到 [nacos-discovery-consumer-example](https://github.com/alibaba/spring-cloud-alibaba/tree/2022.x/spring-cloud-alibaba-examples/nacos-example/nacos-discovery-example/nacos-discovery-consumer-example) 项目的主类 ConsumerApplication，执行 main 方法启动应用。
   - 打包编译后启动：在 [nacos-discovery-consumer-example](https://github.com/alibaba/spring-cloud-alibaba/tree/2022.x/spring-cloud-alibaba-examples/nacos-example/nacos-discovery-example/nacos-discovery-consumer-example) 项目中执行 mvn clean package 将工程编译打包，然后执行 java -jar nacos-discovery-consumer-example.jar 启动应用。

#### 验证

1. 请求 http://127.0.0.1:18083/echo-rest/1234 地址，可以看到响应显示了 nacos-discovery-provider-example 返回的消息 “hello Nacos Discovery 1234”，证明服务发现生效。

   Terminal window

   ```sh
   $ curl http://127.0.0.1:18083/echo-rest/1234
   ```

   响应结果：

   ```sh
   hello Nacos Discovery 1234
   ```

2. 请求 http://127.0.0.1:18083/echo-feign/12345 地址，可以看到响应显示了 nacos-discovery-provider-example 返回的消息 “hello Nacos Discovery 12345”，证明服务发现生效。

   Terminal window

   ```sh
   $ curl http://127.0.0.1:18083/echo-feign/12345
   ```

   响应结果：

   ```sh
   hello Nacos Discovery 12345
   ```

Nacos 服务注册与发现示例源码参考：[Nacos 服务注册与发现示例](https://github.com/alibaba/spring-cloud-alibaba/tree/2022.x/spring-cloud-alibaba-examples/nacos-example/nacos-discovery-example)



------



# 进阶指南

本章节展示 spring-cloud-starter-alibaba-nacos-config 和 spring-cloud-starter-nacos-discovery 的高级特性和进阶用法。

## Nacos 配置中心进阶指南

### profile 粒度配置

spring-cloud-starter-alibaba-nacos-congig 在加载服务配置时：

不仅仅加载了以  dataId 为 ${spring.application.name}.${file-extension:properties} 为前缀的基础配置，还加载了 dataId 为 ${spring.application.name}-${profile}.${file-extension:properties } 的基础配置。

在日常开发中如果遇到多套环境下的不同配置，可以通过 Spring 提供的 ${spring.profiles.active} 这个配置项选择不同情况下的配置。

```properties
spring.profiles.active=develop
```

Nacos 上新增一个 dataId 为：nacos-config-develop.yaml 的基础配置，如下所示：

```yaml
Data ID: nacos-config-develop.yaml
Group: DEFAULT_GROUP
配置格式: YAML
配置内容: current.env: develop-env
```

启动 Spring Boot 应用测试的代码如下：

```java
@SpringBootApplication
public class ProviderApplication {

    public static void main(String[] args) {
        ConfigurableApplicationContext applicationContext = SpringApplication.run(ProviderApplication.class, args);
        while(true) {
            String userName = applicationContext.getEnvironment().getProperty("user.name");
            String userAge = applicationContext.getEnvironment().getProperty("user.age");
            //获取当前部署的环境
            String currentEnv = applicationContext.getEnvironment().getProperty("current.env");
            System.err.println("in "+currentEnv+" enviroment; "+"user name :" + userName + "; age: " + userAge);
            TimeUnit.SECONDS.sleep(1);
        }
    }
}
```

控制台输出结果如下：

```sh
in develop-env enviroment; user name :nacos-config-yaml-update; age: 68

2018-11-02 15:34:25.013 INFO 33014 --- [ Thread-11] ConfigServletWebServerApplicationContext : Closing org.springframework.boot.web.servlet.context.AnnotationConfigServletWebServerApplicationContext@6f1c29b7: startup date [Fri Nov 02 15:33:57 CST 2018]; parent: org.springframework.context.annotation.AnnotationConfigApplicationContext@63355449
```

如果需要切换到生产环境，只需要更改 ${spring.profiles.active} 参数配置即可。如下所示：

```properties
spring.profiles.active=product
```

同时生产环境上 Nacos 需要添加对应 dataId 的基础配置。例如，在生成环境下的 Nacos 添加了 dataId 为：nacos-config-product.yaml 的配置：

```yaml
Data ID: nacos-config-product.yaml

Group: DEFAULT_GROUP

配置格式: YAML

配置内容: current.env: product-env
```

启动测试程序，输出结果如下：

```sh
in product-env enviroment; user name :nacos-config-yaml-update; age: 68

2018-11-02 15:42:14.628 INFO 33024 --- [Thread-11] ConfigServletWebServerApplicationContext : Closing org.springframework.boot.web.servlet.context.AnnotationConfigServletWebServerApplicationContext@6aa8e115: startup date [Fri Nov 02 15:42:03 CST 2018]; parent: org.springframework.context.annotation.AnnotationConfigApplicationContext@19bb07ed
```

> Note：
>
> 此案例中我们通过 `spring.profiles.active=<profilename>` 的方式写死在配置文件中，而在真正的项目实施过程中这个变量的值是需要不同环境而有不同的值。这个时候通常的做法是通过 `-Dspring.profiles.active=<profile>` 参数指定其配置来达到环境间灵活的切换。



### 自定义 Namespace 的配置

Nacos 内部有 [Namespace](https://nacos.io/zh-cn/docs/concepts.html) 的概念:

> 用于进行租户粒度的配置隔离。不同的命名空间下，可以存在相同的 Group 或 Data ID 的配置。Namespace 的常用场景之一是不同环境的配置的区分隔离， 例如开发测试环境和生产环境的资源（如配置、服务）隔离等。 在没有明确指定 ${spring.cloud.nacos.config.namespace} 配置的情况下， 默认使用的是 Nacos 中 public 命名空间即默认的命名空间。如果需要使用自定义的命名空间，可以通过以下配置来实现：

```properties
spring.cloud.nacos.config.namespace=YOUR_NAMESPACE_ID
```

> NOTE:
>
> **该配置必须放在 bootstrap.properties 文件中**。此外 spring.cloud.nacos.config.namespace 的值是 namespace 对应的 id，id 值可以在 Nacos 的控制台获取。并且在添加配置时注意不要选择其他的 namespace，否则将会导致读取不到正确的配置。

### 自定义 Group 的配置

在没有明确指定 ${spring.cloud.nacos.config.group} 配置的情况下， 默认使用的是组 DEFAULT_GROUP 。如果需要自定义 Group，可以通过以下配置来实现：

```properties
spring.cloud.nacos.config.group=YOUR_GROUP_NAME
```

> NOTE:
>
> **该配置必须放在 bootstrap.properties 文件中。**并且在添加配置时 Group 的值一定要和 spring.cloud.nacos.config.group 的配置值一致。

### 配置的优先级

Nacos Config 目前提供了三种配置能力从 Nacos 拉取相关的配置：

- A: 通过 spring.cloud.nacos.config.shared-dataids 支持多个共享 Data Id 的配置
- B: 通过 spring.cloud.nacos.config.ext-config[n].data-id 的方式支持多个扩展 Data Id 的配置
- C: 通过内部相关规则(应用名、应用名+ Profile )自动生成相关的 Data Id 配置

当三种方式共同使用时，他们的一个优先级关系是: ***A < B < C\***

### springc.config.import 引入

这里假设有一个配置文件 bootstrap.yml，升级到 2021.0.1.0 以上的版本应该怎么配置呢？

bootstrap.yml

```yaml
spring:
  cloud:
    nacos:
      config:
        name: test.yml
        group: DEFAULT_GROUP
        server-addr: 127.0.0.1:8848
        extension-configs:
          - dataId: test01.yml
            group: group_01
          - dataId: test02.yml
            group: group_02
            refresh: false
```

**注意：上面的配置和下面的配置是等价的！**

application.yml

```yaml
spring:
  cloud:
    nacos:
      config:
        group: DEFAULT_GROUP
        server-addr: 127.0.0.1:8848
  config:
    import:
      - optional:nacos:test.yml # 监听 DEFAULT_GROUP:test.yml
      - optional:nacos:test01.yml?group=group_01 # 覆盖默认 group，监听 group_01:test01.yml
      - optional:nacos:test02.yml?group=group_02&refreshEnabled=false # 不开启动态刷新
      - nacos:test03.yml # 在拉取nacos配置异常时会快速失败，会导致 spring 容器启动失败
```

使用 spring.config.import 引入配置时的注意事项如下：

1. 如果使用 spring.config.import 就不能使用 bootstrap.yml/properties 引入配置的方式了；
2. 如果引入了 spring-cloud-starter-alibaba-nacos-config，并且使用 import 方式导入配置, 项目启动时会自动检测是否引入了 nacos 条目，如果没有 import nacos 条目，会出现如下错误：

```sh
The spring.config.import property is missing a nacos: entry
Action:
Add a spring.config.import=nacos: property to your configuration.If configuration is not required add spring.config.import=optional:nacos: instead.To disable this check, set spring.cloud.nacos.config.import-check.enabled=false.
```

可以通过手动设置 spring.cloud.nacos.config.import-check.enabled=false 关闭它，但是不建议这么做，这个功能可以帮助你检查是否引入多余依赖

假如想保留以前的使用方式 ( bootstrap 引入配置)，你只需要添加依赖 spring-cloud-starter-bootstrap 依赖，不需要修改一行代码即可完成配置方式的切换！



### 配置项参考

更多关于 spring-cloud-starter-alibaba-nacos-config 的 starter 配置项如下所示:



| 配置项                    | key                                       | 默认值                     | 说明                                                         |
| ------------------------- | ----------------------------------------- | -------------------------- | ------------------------------------------------------------ |
| 服务端地址                | spring.cloud.nacos.config.server-addr     |                            | 服务器 ip 和端口                                             |
| DataId 前缀               | spring.cloud.nacos.config.prefix          | ${spring.application.name} | DataId 的前缀，默认值为应用名称                              |
| Group                     | spring.cloud.nacos.config.group           | DEFAULT_GROUP              |                                                              |
| DataId 后缀及内容文件格式 | spring.cloud.nacos.config.file-extension  | properties                 | DataId 的后缀，同时也是配置内容的文件格式，目前只支持 properties |
| 配置内容的编码方式        | spring.cloud.nacos.config.encode          | UTF-8                      | 配置的编码                                                   |
| 获取配置的超时时间        | spring.cloud.nacos.config.timeout         | 3000                       | 单位为 ms                                                    |
| 配置的命名空间            | spring.cloud.nacos.config.namespace       |                            | 常用场景之一是不同环境的配置的区分隔离，例如开发测试环境和生产环境的资源隔离等。 |
| AccessKey                 | spring.cloud.nacos.config.access-key      |                            |                                                              |
| SecretKey                 | spring.cloud.nacos.config.secret-key      |                            |                                                              |
| 相对路径                  | spring.cloud.nacos.config.context-path    |                            | 服务端 API 的相对路径                                        |
| 接入点                    | spring.cloud.nacos.config.endpoint        |                            | 地域的某个服务的入口域名，通过此域名可以动态地拿到服务端地址 |
| 是否开启监听和自动刷新    | spring.cloud.nacos.config.refresh-enabled | true                       |                                                              |
| 集群服务名                | spring.cloud.nacos.config.cluster-name    |                            |                                                              |



### Endpoint 信息

请求 http://127.0.0.1:18083/actuator/nacosconfig 地址，可以看到相关的 EndPoint 节点信息。

Terminal window

```sh
$ curl http://127.0.0.1:18083/actuator/nacosconfig
```

响应结果：

```json
{

  "NacosConfigProperties": {

    "serverAddr": "127.0.0.1:8848",

    "username": "",

    "password": "",

    "encode": null,

    "group": "DEFAULT_GROUP",

    "prefix": "PREFIX",

    "fileExtension": "properties",

    "timeout": 3000,

    "maxRetry": null,

    "configLongPollTimeout": null,

    "configRetryTime": null,

    "enableRemoteSyncConfig": false,

    "endpoint": null,

    "namespace": "NAMESPACE",

    "accessKey": null,

    "secretKey": null,

    "ramRoleName": null,

    "contextPath": null,

    "clusterName": null,

    "name": null,

    "sharedConfigs": null,

    "extensionConfigs": null,

    "refreshEnabled": true,

    "configServiceProperties": {

      "encode": "",

      "secretKey": "",

      "serveraddr": "127.0.0.1:8848",

      "prefix": "PREFIX",

      "configLongPollTimeout": "",

      "maxRetry": "",

      "password": "",

      "configRetryTime": "",

      "endpoint": "",

      "serverAddr": "127.0.0.1:8848",

      "accessKey": "",

      "enableRemoteSyncConfig": "false",

      "clusterName": "",

      "namespace": "NAMESPACE",

      "ramRoleName": "",

      "username": "",

      "group": "DEFAULT_GROUP"

    },

    "refreshableDataids": null,

    "extConfig": null,

    "sharedDataids": null

  },

  "RefreshHistory": [],

  "Sources": [

    {

      "lastSynced": "2023-05-10 09:35:50",

      "dataId": "nacos-config-example.properties"

    }

  ]

}
```

## Nacos 服务注册与发现进阶指南

### 原理

spring-cloud-starter-alibaba-nacos-discovery 遵循了 Spring Cloud Common 标准，实现了 AutoServiceRegistration、ServiceRegistry、Registration 这三个接口。

在 Spring Cloud 应用的启动阶段，监听了 WebServerInitializedEvent 事件，当 Web 容器初始化完成后，即收到 WebServerInitializedEvent 事件后，会触发注册的动作，调用 ServiceRegistry 的 register 方法，将服务注册到 Nacos Server。

### IPv4 至 IPv6 地址迁移方案

**IPv4 和 IPv6 地址双注册**

在配置完成 Spring Cloud Loadbalancer 作为负载均衡策略后，应用启动后会默认将微服务的 IPv4 地址和 IPv6 地址注册到注册中心中，其中 IPv4 地址会存放在 Nacos 服务列表中的 IP 字段下， IPv6 地址在 Nacos 的 metadata 字段中，其对应的 Key 为 IPv6 。当服务消费者调用服务提供者时，会根据自身的 IP 地址栈支持情况，选择合适的 IP 地址类型发起服务调用。

具体规则：

1. 服务消费者本身支持 IPv4 和 IPv6 双地址栈或仅支持 IPv6 地址栈的情况下，服务消费者会使用服务提供的 IPv6 地址发起服务调用，IPv6 地址调用失败且服务本身同时支持 IPv4 地址栈时，暂不支持切换到 IPv4 地址发起重试调用；
2. 服务消费者本身仅支持 IPv4 单地址栈的情况下，服务消费者会使用服务提供的 IPv4 地址发起服务调用。

**仅注册 IPv4**

如果您只想使用 IPv4 地址进行注册，可以在 application.properties 使用如下配置项进行配置：

```properties
spring.cloud.nacos.discovery.ip-type=IPv4
```

**仅注册 IPv6**

如果您只想使用 IPv6 地址，可以在 application.properties 使用如下配置项进行配置：

```properties
spring.cloud.nacos.discovery.ip-type=IPv6
```

### 配置项参考

更多关于 spring-cloud-starter-alibaba-nacos-discovery 的 starter 配置项如下所示:

| 配置项                | key                                                      | 默认值   | 说明                                                         |
| --------------------- | -------------------------------------------------------- | -------- | ------------------------------------------------------------ |
| 服务端地址            | spring.cloud.nacos.discovery.server-addr                 |          |                                                              |
| 服务名                | spring.cloud.nacos.discovery.service                     | 应用名   | 注册到 Nacos 上的服务名称，默认值为应用名称                  |
| 权重                  | spring.cloud.nacos.discovery.weight                      | 1        | 取值范围 1 到 100，数值越大，权重越大                        |
| 网卡名                | spring.cloud.nacos.discovery.network-interface           |          | 当 IP 未配置时，注册的 IP 为此网卡所对应的 IP 地址，如果此项也未配置，则默认取第一块网卡的地址 |
| 注册的 IP 地址        | spring.cloud.nacos.discovery.ip                          |          | 优先级最高                                                   |
| 注册的 IP 地址类型    | spring.cloud.nacos.discovery.ip-type                     | 双栈地址 | 可以配置 IPv4 和 IPv6 两种类型，如果网卡同类型 IP 地址存在多个，希望制定特定网段地址，可使用`spring.cloud.inetutils.preferred-networks`配置筛选地址 |
| 注册的端口            | spring.cloud.nacos.discovery.port                        | -1       | 默认情况下不用配置，会自动探测                               |
| 命名空间              | spring.cloud.nacos.discovery.namespace                   |          | 常用场景之一是不同环境的注册的区分隔离，例如开发测试环境和生产环境的资源（如配置、服务）隔离等。 |
| AccessKey             | spring.cloud.nacos.discovery.access-key                  |          |                                                              |
| SecretKey             | spring.cloud.nacos.discovery.secret-key                  |          |                                                              |
| Metadata              | spring.cloud.nacos.discovery.metadata                    |          | 使用 Map 格式配置                                            |
| 日志文件名            | spring.cloud.nacos.discovery.log-name                    |          |                                                              |
| 集群                  | spring.cloud.nacos.discovery.cluster-name                | DEFAULT  | Nacos 集群名称                                               |
| 接入点                | spring.cloud.nacos.discovery.endpoint                    |          | 地域的某个服务的入口域名，通过此域名可以动态地拿到服务端地址 |
| 是否集成 LoadBalancer | spring.cloud.loadbalancer.nacos.enabled                  | false    |                                                              |
| 是否开启 Nacos Watch  | spring.cloud.nacos.discovery.watch.enabled               | false    | 可以设置成 true 来开启 watch                                 |
| 是否启用 Nacos        | spring.cloud.nacos.discovery.register-enabled            | true     | 默认启动，设置为 false 时会关闭自动向 Nacos 注册的功能       |
| 是否启用容错配置      | `spring.cloud.nacos.discovery.failure-tolerance-enabled` | false    | 开启 nacos 服务发现失败容错能力，该功能会在 nacos 获取实例失败时返回上一次获取的实例，可以在 nacos server 网络不稳定时提供容错能力，不会导致请求全部挂掉 |

### Endpoint 信息

请求 http://127.0.0.1:18083/actuator/nacosdiscovery 地址，可以看到相关的 EndPoint 节点信息。

Terminal window

```sh
$ curl http://127.0.0.1:18083/actuator/nacosdiscovery
```

响应结果：

```json
{

  "subscribe": [],

  "NacosDiscoveryProperties": {

    "serverAddr": "127.0.0.1:8848",

    "username": "nacos",

    "password": "nacos",

    "endpoint": "",

    "namespace": "",

    "watchDelay": 30000,

    "logName": "",

    "service": "service-consumer",

    "weight": 1,

    "clusterName": "DEFAULT",

    "group": "DEFAULT_GROUP",

    "namingLoadCacheAtStart": "false",

    "metadata": {

      "IPv6": null,

      "preserved.register.source": "SPRING_CLOUD"

    },

    "registerEnabled": true,

    "ip": "192.168.3.19",

    "networkInterface": "",

    "ipType": null,

    "port": 18083,

    "secure": false,

    "accessKey": "",

    "secretKey": "",

    "heartBeatInterval": null,

    "heartBeatTimeout": null,

    "ipDeleteTimeout": null,

    "instanceEnabled": true,

    "ephemeral": true,

    "failureToleranceEnabled": false,

    "failFast": true,

    "nacosProperties": {

      "password": "nacos",

      "endpoint": "",

      "secretKey": "",

      "serverAddr": "127.0.0.1:8848",

      "accessKey": "",

      "clusterName": "DEFAULT",

      "namespace": "",

      "com.alibaba.nacos.naming.log.filename": "",

      "namingLoadCacheAtStart": "false",

      "failFast": "true",

      "username": "nacos"

    }

  }

}
```









