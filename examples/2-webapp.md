## 使用Maven创建Web工程

创建一个web工程和创建一个普通工程差不多

```bash
$ mvn archetype:generate

。。。
10: internal -> org.apache.maven.archetypes:maven-archetype-webapp (An archetype which contains a sample Maven Webapp project.)
Choose a number or apply filter (format: [groupId:]artifactId, case sensitive contains): 7: 10
# 这里，我们选择第十个webapp作为我们的模板

# 其他的和之前一样
```

### 目录结构

``` bash
tree
.
├── pom.xml
└── src
    └── main
        ├── resources
        └── webapp
            ├── WEB-INF
            │   └── web.xml
            └── index.jsp

5 directories, 3 files
```

和之前一样，就是多了一个webapp的目录，这里就是存放我们之前使用tomcat需要的一些文件。

到时候打包的时候，就会把class文件、静态资源一起打包到webapp，然后压缩成war包，到时候我们部署这个war包就行了。

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.github.fish56</groupId>
  <artifactId>HelloMavenWebapp</artifactId>
  <packaging>war</packaging>
  <version>1.0</version>
  <name>HelloMavenWebapp Maven Webapp</name>
  <url>http://maven.apache.org</url>
  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>3.8.1</version>
      <scope>test</scope>
    </dependency>
  </dependencies>
  <build>
    <finalName>HelloMavenWebapp</finalName>
  </build>
</project>
```

和之前没什么变化，就是打包方式变成的war包。



#### 打包

``` bash
$ mvn package

$ tree 
.
├── pom.xml
├── src
│   └── main
│       ├── resources
│       └── webapp
│           ├── WEB-INF
│           │   └── web.xml
│           └── index.jsp
└── target
    ├── HelloMavenWebapp
    │   ├── META-INF
    │   ├── WEB-INF
    │   │   ├── classes
    │   │   └── web.xml
    │   └── index.jsp
    ├── HelloMavenWebapp.war
    ├── classes
    └── maven-archiver
        └── pom.properties
```

