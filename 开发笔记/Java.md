# Java

## 安装-win

- 下载：官网下载jdk的exe文件
- 安装：双击直接安装
- 检测：cmd键入`java`，显示帮助手册

## 配置系统环境变量-win

- 目的：将jdk下的bin目录添加到系统变量PATH底下
- 操作：一般创建一个名为JAVA_HOME的环境变量，值为jdk目录，然后在PATH里添加上该变量的bin目录
- 检测：cmd键入`javac`，显示帮助手册

## 安装-linux

- 安装jdk8：`yum install openjdk-8-jdk`，中途询问添加环境变量键入`yes`
- 检测：`java -version`显示版本则成功
