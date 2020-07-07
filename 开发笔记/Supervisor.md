# supervisor

## 简介

supervisor是进程监控工具，被监控的应用一旦挂了，会自动被拉起

## 安装

- 安装：`yum install supervisor`
- 检测：`supervisord -h`，出现帮助手册则安装成功

## 配置

### 主配置文件supervisor.conf

- 一般不做更改，如果要使用web监控界面，可打开一下注释（注意，为了安全最好不用对公网暴漏）

```ini
[inet_http_server]          ;web管理界面的HTTP服务器
port=127.0.0.1:9001         ;Web界面服务的IP（不要写localhost）和端口
username=user               ;登录管理后台的用户名
password=123                ;登录管理后台的密码
```

- 日志文件目录，可查看启动日志。日志超过大小会新建日志文件，原日志文件备份为后缀`.n`，数字越小越新

```ini
[supervisord]
logfile=/var/log/supervisor/supervisord.log  ; 日志文件目录
logfile_maxbytes=50MB        ;日志文件大小，超出会rotate，默认 50MB)
logfile_backups=10            ;日志文件保留备份数量默认10，设为0表示不备份
loglevel=info                ;日志级别，默认info，其它: debug,warn,trace
pidfile=/var/run/supervisord.pid  ;pid 文件
nodaemon=false               ;是否在前台启动，即以daemon的方式启动
minfds=1024                  ;可以打开的文件描述符的最小值
minprocs=200                 ;可以打开的进程数的最小值
```

- 子配置文件目录，一般所有进出的配置目录在此处配置

```ini
[include]
files = supervisord.d/*.ini    ;配置文件目录
```

### 进程的配置文件

- 在主配置文件指定的目录下创建.ini文件后，会自动检测并加载
- 示例：demo.ini

```ini
[program:demo]             ;项目名
command=java -jar demo.jar    ;执行的命令
stderr_logfile=/home/jeeson/error_demo.log        ;错误日志
stdout_logfile=/home/jeeson/demo.out        ;输出日志
directory=/home/jeeson        ;项目路径
autostart=true        ;当supervisor 启动时会自动启动，默认为3次
user=root        ;用户
autorestart=true        ;自动重启
```

- 使用测试：kill进程后查看进程的pid是否更换

## 服务告警

### superlance安装

- 安装superlance: `pip install superlance`
- 检测：`httpok`，出现帮助手册则成功

### sendemail邮件告警

- 如果不安装sendeamil，默认会使用linux自带的发送邮件，发送出去的邮件很容易隐藏自己的信息，所以一般邮件服务商针对这些邮件会报错.
- 安装：`yum install sendemail`
- 检测：`sendemail -h`，出现帮助手册则成功
- 配置：在主文件的目录下创建.ini文件，将邮件告警服务作为一个进程被supervisor管理

### 服务停止告警

- 示例：demo_crashmail.ini
  
  ```ini
  [eventlistener:demo_crashmail]     ;监听器名称  
  command=crashmail -p demo -m 1937811400@qq.com ;发送邮件的命令
  events=PROCESS_STATE_EXITED        ;监听的事件，此处为退出
  redirect_stderr=false              ;把stderr 重定向到stdout
  ```

- 命令说明：PROCESS_STATE_EXITED是退出时触发命令，命令crashmail是发送邮件，-p指定监控的进程（需是进程的.ini配置文件中的program名称），-m指定邮箱，
- 使用测试：kill被监控进程后查看邮箱是否收到邮件

### 服务内存监控告警

- 示例：demo_mommon.ini
  
  ```ini
  [eventlistener:demo_memmon]
  command=memmon -p demo=1MB -m 1937811400@qq.com
  events=TICK_60
  redirect_stderr=false
  ```

- 命令说明：TICK_60是每60秒间隔触发一次命令，命令memmon是查询占用内存的情况，并会在满足条件时（内存占用高于设定值）重启进程，发送告警邮件，-P指定监控的进程，后面是规定的内存大小，-m指定邮箱

## 命令

### 启停

- 启动：`systemctl start supervisord`
- 状态：`systemctl status supervisord`
- 开机自启动：`systemctl enable supervisord`

### 管理

- 有两种方式，一种是每个操作前加上`supervisorctl`，例如`supervisorctl status`，另一种是输入`supervisorctl`进入终端，直接输入响应命令无需前缀，例如`status`。退出终端`quit`
- 退出终端：`quit`
- 查看状态：`status`
