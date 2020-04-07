# Ubuntu

## 操作系统

- 镜像：官网网速慢，使用[阿里云](http://mirrors.aliyun.com/ubuntu-releases/18.04/)
- root密码：`zhangxun`
- 用户jeeson，密码`jeeosn`

## 系统使用

### 初次设置root密码

- `sudo passwd root`
- 输入当前用户密码
- 输入root用户密码
-再次 输入root用户密码

### root用户切换

- `su`
- 输入root用户密码
- `exit`退出root用户

### 更改源

- 【软件和更新】-->【下载自】选择阿里云（aliyun）
- `apt-get upgrade`　--> `apt-get update`

### 软件安装

- 下载deb包 XXX.rpm
-界面安装： 双击的deb包，自动的打开应用商店进行安装，此方法会自动解决依赖
- 命令行安装：`dpkg  -i XXX.deb`
  - 如果依赖报错，先执行`apt-get -f --fix--missing install`
  - 如果`apt-get -f`报错，先执行`apt-get update`
  - 再执行`apt-get install -f`，最后执行`dpkg -i XXX.deb`

## 软件

- 搜狗输入法
  - 搜狗输入法需要fcitx的支持
  - 首先【打开语言和地区】-->【管理已安装的语言】，如果报错则需要执行`apt-get install -f --fix-missing`，如果该命令报错，则需要再先执行`apt-get update`，执行完后就可以在应用里发现fcitx已安装好了，
  - 安装搜狗输入法的deb包
  - 再打开【管理已安装的语言】，按提示安装缺失的语言字体，【键盘输入法系统】选择fcitx，**注意**：需将搜狗拼音放在第二位，否则会出现选字栏乱码的现象
  - reboot重启
  - 中文状态下打出的英文空格太大：shift + space切换到半圆角
- shadowsockes-qt5(需要服务器地址)
  - 添加源：`add-apt-repository ppa:hzwhuang/ss-qt5`
  - 修改源的发行版：打开【软件和更新】–>【其他软件】,找到`http://ppa.launchpad.net/hzwhuang/ss-qt5/ubuntu bionic Release`-->【编辑】，将发行版从 bionic改为artful
  - 更新源：`apt-get upgrade`
  - 安装:`apt-get install shadowsocks-qt5`
- chrome
- 蓝灯
- wps
- 网易云音乐
- 百度网盘
- VScode
- vbox
- QQ

## 编程

- nodejs
- python
- java

### 添加开机启动

- 【启动应用程序】-->【添加】-->【命令】填入sh脚本地址，保存

### 快捷键

- 多任务：win键
- 终端：ctrl+alt+t
- 回到桌面：ctrl + alt + d
