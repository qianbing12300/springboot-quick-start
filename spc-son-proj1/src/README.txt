1.项目启动时候如何选择dev环境还是prod环境?
第一种:在application.yml环境中配置,其中---代表分隔的是文档
server:
  servlet:
    context-path: /bootMultiProfiles
spring:
  profiles:
    active: dev
---
spring:
  profiles: prod
server:
  port: 8081
---
spring:
  profiles: dev
server:
  port: 8082

第二种:在命令行中利用命令配置
-Dspring.profiles.active=prod

第三种:在maven对应模块里Lifecycle先clean,再package.
-- application-dev.yml
    spring:
      profiles: dev
    server:
      port: 8888
      servlet:
        context-path: /bootMultiProfiles4dev

--application-prod.yml
    spring:
      profiles: prod
    server:
      port: 9999
      servlet:
        context-path: /bootMultiProfiles4prod

进入命令行，执行jar命令
java -jar spcsonproj1.jar --spring.profiles.active=dev
运行成功后,会显示对应的环境运行的端口号.


启动时如何设置JVM各种参数？
java -Xms128m -Xmx128m -jar spcsonproj1.jar --server.port=8888

如何查找配置的参数？
1. jps 查看进程
 如 20744  jar
2. jinfo 20744 chakan
