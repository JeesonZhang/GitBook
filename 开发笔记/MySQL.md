# MySQL

## 安装-linux

- 安装：目前mysql支持yum直接安装，所以需要先下载yum源
  - 下载官方yum源：`rpm -ivh http://dev.mysql.com/get/mysql-community-release-el7-5.noarch.rpm`
  - 安装：`yum install mysql-server`
- 检测：键入`yum list installed | grep mysql`有对应输出
- ps：使用systemctl命令进行服务管理时建议使用`mysqld`，因为禁止开机启动后，`mysql`会找不到

## 命令

- 设置密码：
  - `use user`
  - `update user set password=password('password') where user='root';`
  - 重启mysql服务
- 开放可访问机器
  - `update user set host = '%' where user = 'root' and host = 'localhost';`：修改机器权限
  - `flush privileges;`：刷新权限
