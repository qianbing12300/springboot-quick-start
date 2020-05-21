如何将项目打包成war包？
1. <!--第一步：pom里面jar包改成war-->
<packaging>war</packaging>

2. <!--第二步：spring-boot-starter-tomcat中scope需要改成provided-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-tomcat</artifactId>
            <scope>provided</scope>
        </dependency>

3.启动类继承SpringBootServletInitializer,并实现configure()方法.
@SpringBootApplication
public class SpcSonWarApplication extends SpringBootServletInitializer {

    public static void main(String[] args) {
        SpringApplication.run(SpcSonWarApplication.class, args);
    }

    @Override
    protected SpringApplicationBuilder configure(SpringApplicationBuilder builder) {
        return builder.sources(SpcSonWarApplication.class);
    }
}

4. 可选: 用户指定名称打包build里面 <finalName>spcsonwar</finalName>
5. 注意：run configuration---> tomcat server --> deployment --> Application context ---> 增加 /spcsonwar

请求地址：http://localhost:8080/spcsonwar/hello/