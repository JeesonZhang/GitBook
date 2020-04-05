# GitBook

## 安装

### 安装nodejs

- 安装：`apt install nodejs`
- 检测：`node -v`显示版本号则成功

### 安装npm

- 安装：`apt install npm`
- 检测：`npm -v`显示版本号则成功
- 切换淘宝源：`npm config set registry https://registry.npm.taobao.org`

### 安装GitBook

- 安装：`npm install gitboook-cli -g`
- 检测：`gitbook -Ｖ`显示版本号则成功，如果不是最新版本则会自动更新

## 使用

- 创建：进入某个目录，`gitbook init`将该目录初始化为gitbook项目
- 运行：`gitbook serve`运行项目，默认在本地的4000端口打开，可通过浏览器访问

## 结构

- README.md：当前目录的介绍文件，每个目录都带有，用于标识目录位置
- SUMMARY.md：目录文件，语法：`* [目录名](链接的md文件路径)`
- _book：目录的属性配置文件

## 配置

- book.json：推荐创建book.json用于做配置管理

```json
{
　　"配置项":  "配置值"
}
```

### 插件

- 添加配置：在book.josn文件中添加`plugins`列表，列表中即配置插件名称
- 插件安装：在项目主目录下执行`gitbook install`，会自动根据book.json中配置的插件安装插件，并生成node_modules目录，安装的插件会放在此目录下
- 常用插件

```json
{
    "plugins":[
        "chapter-fold" 　// 自动折叠目录
    ]
}
```
