# linux

## GUI打不开部分应用，报错failed to execute child process "gnome-XXX"

- 原因：gnome界面的一些代码使用python写的，所有找不到正确地Python3命令执行
- 解决：为/usr/bin下的Python3.6创建python3软连接：`ln -s /usr/bin/python3.6  /usr/bin/python3`
