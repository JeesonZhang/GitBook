# Maven

## 简介

- 介绍：Maven是jar包管理工具

## 安装-win

- 下载：[官网](https://maven.apache.org/download.cgi)直接下载binary.zip（**注:3.6.2和idea可能会有兼容问题，因此推荐下载[3.6.1](http://apache.mirror.amaze.com.au/maven/maven-3/)**）
- 安装：配置环境变量（Path:maven目录/bin）
- 检测：cmd键入`maven -v`显示版本则成功

### 安装-Linux

- 下载：`yum install maven`
- 检测：`mvn -v`显示版本则成功

## 基本配置

- 配置`maven目录\conf\settings.xml`
  - 配置本地仓库位置：注意文件分割符的方向

    ```xml
    <!-- 本地仓库位置 -->
    <settings>
      <localRepository>C:\Maven\m2\repo</localRepository>
    </settings>
    ```

  - 配置镜像源

    ```xml
    <!-- 阿里云镜像 -->
    <mirrors>
      <mirror>
        <id>alimaven</id>
        <name>aliyun maven</name>
        <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
        <mirrorOf>central</mirrorOf>
     </mirror>
    </mirrors>
    ```

## pom.xml解读

- `properties`：自定义属性
- `scope`：作用域
  - `test`：测试
  - `provided`：已经提供

## 其他

- maven的classpath指resource目录

## 打包

### 依赖

- 会打出两个jar包，带依赖的和带依赖的
  
```xml
  <plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-assembly-plugin</artifactId>
    <version>2.5.5</version>
    <configuration>
        <archive>
            <manifest>
                <mainClass>主类(com.yisa.App)</mainClass>
            </manifest>
        </archive>
        <descriptorRefs>
            <descriptorRef>jar-with-dependencies</descriptorRef>
        </descriptorRefs>
    </configuration>
    <executions>
        <execution>
            <id>make-assembly</id>
            <phase>package</phase>
            <goals>
                <goal>single</goal>
            </goals>
        </execution>
    </executions>
  </plugin>
```

- 下面依赖解决编码问题，将源码、输入、输出都配置为UTF-8

```xml
  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
    <maven.compiler.encoding>UTF-8</maven.compiler.encoding>
  </properties>
```

### 命令

- 打包执行：`mvn assembly:assembly`
- 运行jar包执行：`java -jar XXX`
- linux上退出终端不中止进程：`nohup java -jar 要运行的jar包 > 日志文件目录 2>&1 &`（例如：`nohup java -jar renren-fast.jar > /home/zhangxun/logs 2>&1 &`）
- 可通过反编译工具（例如JD_Gui），根据jar包获取源码，但可能会有些许出入
- 重新打包需先`clean`
