如何新建一个springBoot聚合项目？
1. 新建父项目
   file --> project -->spring initializr --> next --> project metedata(Group: com.suning/Aitifact:
   springboot-parent-project/type: 选择  Maven Pom) ---> dependencies(web->spring web starter)-->next --> finish

父pom修改
    <artifactId>spring-boot-starter-parent</artifactId>版本号建议适量修改为1.0.3版本即可.

2. 新建子模块module
   new --> module -->spring initializr --> next --> project metedata(Group: com.suning/Aitifact:
   springboot-parent-project/type: 选择  Maven project) ---> dependencies(web->spring web starter)-->next --> finish

子pom修改父pom来源
    <parent>
        <groupId>com.tuling</groupId>
        <artifactId>spc-parent-proj</artifactId>
        <version>0.0.1-SNAPSHOT</version>
    </parent>

    增加子pom的打包方式 <packaging>jar</packaging>

    子pom打包生产指定名称，增加标签 finalName
    <build>
            <finalName>spcsonproj1</finalName>
            <plugins>
                <plugin>
                    <groupId>org.springframework.boot</groupId>
                    <artifactId>spring-boot-maven-plugin</artifactId>
                </plugin>
            </plugins>
    </build>




