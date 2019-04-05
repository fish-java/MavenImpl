运行一个maven项目基本两个步骤：编译和运行

```bash
$ mvn compile
$ java -cp ~/.m2/repository:./target/classes Hello
```

运行的时候还是比较麻烦的，需要指定仓库和编译后文件的目录，以及程序入口。