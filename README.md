# SpringCloudAll
Spring Cloud Alibaba 解决方案 —— 学习示例代码

### 技术体系【知识点】


- 1、Nacos 服务注册和发现
- 2、Nacos 统一配置中心
- 3、熔断降级限流 sentinel
- 4、feign配合sentinel使用
- 5、SpringCloud Gateway
- 6、服务监控 actuator
- 7、Spring Boot Admin服务监控
- 8、链路跟踪 skywalking
- 9、Spring Security集成
- 10、Spring Security OAuth2集成
- 11、rabitmq的环境搭建和使用
- 12、maven多配置环境
- 13、服务多实例运行
- 14、分布定时任务 Quartz/XXL-JOB/elastic-job
- 15、Seata分布式事务
- 16、Spring Stream
- 17、分布式文件系统 minio、阿里OSS

### 常用注解

 注解 | 功能 | 位置 
 -|-|- 
@EnableDiscoveryClient   | 启动nacos服务注册发现| 启动类 |
@EnableFeignClients   | 启动 Feign| 启动类 |
@FeignClient  | 声明为Feign接口 | 接口类 |
@EnableAdminServer| Spring Boot Admin Server监控服务端 | 启动类 |
@SentinelRestTemplate|  |


### 环境安装
 软件 | 访问地址 | 账号 | 启动
 -|-|-|- 
[nacos安装](https://nacos.io/zh-cn/docs/quick-start-docker.html)  | http://localhost:8848/nacos| nacos/nacos | docker启动容器 |
[sentinel控制台](https://www.cnblogs.com/fx-blog/p/11720220.html)   | http://localhost:8080 |  sentinel/sentinel | 启动命令: java -jar sentinel-dashboard-1.6.3.jar  `本地目录： D:\JAVA\alibaba-cloud`|


### 测试请求

 ``` xml
# 服务端生产者接口（启动多实例）
http://localhost:8061/echo/123
http://localhost:8061/actuator | 服务端点检查
http://localhost:8061/actuator/nacos-discovery | 服务端点检查
## 服务端_多实例测试
http://localhost:8062/echo/123 [修改nacos配置端口，启动多实例]
http://localhost:8063/echo/123 [修改nacos配置端口，启动多实例]


# 客户端消费者接口
http://localhost:8071/cust/echo/feign
http://localhost:8071/cust/echo/restTemplate
## 客户端_多实例测试
http://localhost:8072/cust/echo/feign [修改端口，启动多实例]
http://localhost:8073/cust/echo/feign [修改端口，启动多实例]


# Gateway(需传递 Head参数 => Authorization:{任意值})
http://localhost:9999/echo/22

# SpringAdmin
http://localhost:9112

# Security
http://localhost:9111/user
(admin/123456)
 ```




### 官方文档
- [spring-cloud-alibaba](https://github.com/alibaba/spring-cloud-alibaba/blob/master/README-zh.md)
- [spring-cloud-alibaba > html](https://spring-cloud-alibaba-group.github.io/github-pages/greenwich/spring-cloud-alibaba.html#_introduction_of_sentinel)
- [spring-cloud-gateway](https://cloud.spring.io/spring-cloud-static/spring-cloud-gateway/2.2.2.RELEASE/reference/html/#the-path-route-predicate-factory)
- [spring-security](https://docs.spring.io/spring-security/site/docs/current/reference/html5/#getting)
- [spring-security-oauth](https://projects.spring.io/spring-security-oauth/docs/oauth2.html)
- [Seata 分布式事务](https://seata.io/zh-cn/index.html)
- [Spring Cloud Stream中文指导手册](https://m.wang1314.com/doc/webapp/topic/20971999.html)



### 参考文献
- [微服务后，Swagger接口统一文档](https://blog.csdn.net/qq_31748587/article/details/102563155)
- 谷歌JSON插件 JSON-Handle
- [Spring Boot Admin服务监控](https://www.jianshu.com/p/1749f04105fb)
- [Spring Boot Admin client不再需要](https://my.oschina.net/u/1428688/blog/3110948)
- [Spring Boot Admin+Nacos从入门到上线](https://blog.csdn.net/qq_38496561/article/details/105945386)
- [容器使用Undertow替换tomcat](https://blog.csdn.net/moshowgame/article/details/84985765)
- [Seata分布式事务 整合 SpringCloud](https://seata.io/zh-cn/blog/integrate-seata-with-spring-cloud.html)
- [Gateway 之限流操作  一](https://www.toutiao.com/i6729667803353186827)
- [Gateway 之限流操作  二](https://blog.csdn.net/u010889990/article/details/81169328)
- [Gateway 之限流操作  三](https://www.cnblogs.com/pu20065226/p/11426279.html)
- [Gateway 实现降级攻略](https://blog.csdn.net/SuperBins/article/details/94732087)
- [灰度发布名词解释](https://www.cnblogs.com/panchanggui/p/11634026.html)
- [Nacos动态路由实现](https://www.cnblogs.com/zlt2000/p/11712943.html)





### 技巧与工具
- [在线工具yml和属性互转](https://www.toyaml.com/index.html)
-  yml文件注意（禁用tab，用俩空格）
- 谷歌JSON插件 JSON-Handle
- gateway 支持服务名方式访问
- sentinel 服务台可以不用
- [IDEA如何启动多实例](https://blog.csdn.net/zhou520yue520/article/details/81167841)
- [idea run dashboard](https://blog.csdn.net/m18633778874/article/details/82687389)
- [idea的Git主干同步到分支](https://blog.csdn.net/weixin_40836179/article/details/87003899)