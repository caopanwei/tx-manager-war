# TxManager(v2.0.1)
TxManager是LCN分布式事务框架的事务协调器，框架基于Netty做消息通讯，事务控制数据存储在Redis中。

## 使用教程
1. 启动redis服务


2. 配置application.properties文件

```
#redis
#redis主机地址
spring.redis.hostName=127.0.0.1

#redis主机端口
spring.redis.port=6379
#redis链接密码
spring.redis.password=

spring.redis.pool.maxActive=10
spring.redis.pool.maxWait=-1
spring.redis.pool.maxIdle=5
spring.redis.pool.minIdle=0
spring.redis.timeout=0

#服务端口
server.port=8030
spring.application.name=tx-manager

spring.thymeleaf.prefix=classpath:/html/
spring.thymeleaf.suffix=.html

eureka.instance.hostname=localhost
eureka.client.serviceUrl.defaultZone=http://localhost:8030/eureka/
eureka.client.registerWithEureka=false
eureka.client.fetchRegistry=false


#参与事务的最大等待时间（单位：秒） 所有参与分布式事务逻辑处理的最大等待时间
transaction_wait_max_time = 5

#存储到redis下的数据最大保存时间（单位：秒）
redis_save_max_time = 30

#socket server Socket对外服务端口
socket.port = 9999

#socket ip Socket对外服务IP (主要：必须是外网访问地址)
socket.ip = 192.168.3.102

# 最大socket连接数
socket.max.connection = 100

#开启负载均衡策略 true false
slb.on = false

#开启负载均衡必填项 服务器地址列表

#负载均衡类型 轮训策略:polling
slb.type = polling

#服务器地址列表  说明：中间用#分割(不能写本服务器，不然会出现死循环)端口是指服务端口非socket端口
slb.list = http://127.0.0.1:8889/#http://127.0.0.1:8810/

```

3. 配置完成后启动tomcat。然后访问`http://127.0.0.1:8080/tx-manager-2.0.0-SNAPSHOT/index` 正常如下：

![ ](readme/tx-manager.png)

[tx-manager源码](https://github.com/1991wangliang/tx-lcn/tree/master/tx-manager) 


技术交流群：554855843