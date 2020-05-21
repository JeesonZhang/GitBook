# Git

## 安装

- 安装：`apt install git`
- 检测：`git`，展示相关命令则安装成功

## 连接远端仓库

- 检测本地是否已经生成秘钥：如果当前用户的home目录的.ssh目录下（例如：`~/home/.ssh`）存在id_rsa和id_rsa.pub文件，则已经生成公钥
- 生成秘钥：若尚未生成秘钥，则运行`ssh-keygen -t rsa -C "邮箱"`，后面提示填入密码都可以直接回车，即可生成秘钥文件
- 远端配置SSH key：打开github远端，【Settings】【SSH and GPG key】【New SSH key】，ttile建议填入邮箱，key则粘贴之前生成的id_rsa.pub文件的全部内容
- 检测：`ssh -T git@github.com`，提示【Hi username! You’ve successfully authenticated, but GitHub does not provide shell access.】则成功
- 设置用户名：`git config --global user.name "XXX"`
- 设置邮箱：`git config --global user.email "XXX"`

## 命令

### 撤销

- 撤销修改：`git checkout -- XXX`
  - `.`：所有文件
- 撤销add（从缓存撤销到工作区）：`git reset XXXX`，不指定则撤销所有
- 撤销commit：`git reset HEAD^`
  - HEAD^ 指上一次commit，等价于 HEAD~1，如果撤销后n次commit，则为 HEAD~n
  - `--soft`：撤销commit
  - `--mixed`（默认）：撤销commit和add
  - `--hard`：撤销commit和add，并删除修改的代码

### 分支管理

- 查看分支：`git branch`
  - `-a` 查看所有分支（包括远程）
- 新建本地分支：`git checkout -b XXX`
