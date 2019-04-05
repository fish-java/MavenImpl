## 目录结构
Java社区 有 约定 > 配置 > 编码 的风格。

这是一个maven工程的标准目录结构：

```
.
├── README.md
├── pom.xml
├── src
│   ├── main
│   │   └── java
│   │       └── Hello.java
│   └── test
│       └── java
│           └── Test.java
└── target
    ├── classes
    │   └── Hello.class
    ├── generated-sources
    │   └── annotations
    └── maven-status
        └── maven-compiler-plugin
            └── compile
                └── default-compile
                    ├── createdFiles.lst
                    └── inputFiles.lst
```
- ${basedir}	存放pom.xml和所有的子目录
- ${basedir}/src/main/java	项目的java源代码
- ${basedir}/src/main/resources	项目的资源，比如说property文件，springmvc.xml
- ${basedir}/src/test/java	项目的测试类，比如说Junit代码
- ${basedir}/src/test/resources	测试用的资源
- ${basedir}/src/main/webapp/WEB-INF	web应用文件目录，web项目的信息，比如存放web.xml、本地图片、jsp视图页面
- ${basedir}/target	打包输出目录
- ${basedir}/target/classes	编译输出目录
- ${basedir}/target/test-classes	测试编译输出目录
- **Test.java：	Maven只会自动运行符合该命名规则的测试类**
- ~/.m2/repository	Maven默认的本地仓库目录位置

应为java程序有一个编译的过程，而且它基于包做模块管理，所以他在编译后要保证
- 包目录的一致性
- 通过相对路径引用的资源要保持一致
- 测试文件也不能像nodejs一样通过相对，路径随时添加

所以就有了上面复杂的目录