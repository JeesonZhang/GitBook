# Linux

## 查看硬件信息

## 软链接

- 介绍：软连接用于关联命令，`->`符号标识，左边是输入命令，右边是真是命令地址
- 查看软连接：`ll`
- 设置软连接：`ln -s 真实命令路径 新编命令路径`（例如：`ln -s /usr/bin/python2.7 python`）
- 删除软连接：`rm 软连接`

## 环境变量

- 查看所有环境变量：`export`
- 添加环境变量：`export 变量名=变量值`
- 删除环境变量：`unset 变量名`

## 系统环境变量

- 系统环境变量：系统可直接执行的命令所在的bin目录
- 查看系统环境变量：`echo $PATH`
- 设置系统环境变量：`export PATH=命令的bin目录`
- 修改系统环境便令：`exprot PATH=命令的bin目录`

## 服务管理

- 启动某服务：`systemctl start XXX`
- 重启某服务：`systemctl restart XXX`
- 重新按配置加载某服务：`systemctl reload XXX`
- 停止某服务：`systemctl stop XXX`
- 查看服务状态：`systemctl status XXX`
- 查看是否开机自启动：`systemctl is-enabled XXX`
- 开机启动：`systemctl enable XXXX`
- 禁止开机启动：`systemctl disable XXX`
- 显示启动失败的服务：`systemctl --failed`
