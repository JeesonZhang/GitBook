# Anaconda

## 安装

### Windows下

- 下载：官网慢，可从[清华镜像源](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/)进行下载
- 安装：运行安装程序，中途勾选【添加环境变量】（**注意中途会出现一个黑色的对话框，切记不要关闭，否则会没有jupyter等软件**）
- 检测：`cmd+r`打开命令行，键入`python`后出现解释器即成功，键入`exit()`可退出
- ps：如果忘记勾选【添加环境变量】，那可以手动添加：
  - 添加Anaconda目录即可使用python
  - 添加Anaconda\Scripts目录即可使用conda命令（此时仅可使用`conda --version`命令）
  - 添加【Anaconda3\Library\bin】和【Anaconda3\Library\mingw-w64\bin】后即可使用其他conda命令

### Linux下

- 下载：由于官网网速原因，推荐从[清华镜像源](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/)进行下载，直接下载最新的64位`.sh`文件
- 安装：`.sh`运行sh格式的安装文件，按回车阅读协议，回复`yes`同意协议，对话出现环境变量提示，回复`yes`
- 初始化conda：`source ~/.bashrc`
- 检测：`conda -V`显示conda版本
- 设置环境变量：`export PATH=anaconda目录/bin:$PATH`（例如：`export PATH=/home/jeeson/anaconda3/bin:$PATH`）
- 检测：`anaconda -V`显示anaconda版本

## anaconda常用命令

### 源管理

- 由于官网网速原因，一般会使用国内的包源，源相当于包的远程应用商店
- 查看包源列表：`conda config --show channels`
- 添加镜像源：`conda config --add channels 源地址`（添加清华镜像源：`conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/free/`）
- 删除指定包源：`conda config --remove channels 源地址`
- 删除自己添加的包源：`conda config --remove-key channels`

### 环境管理

- 查看环境：`conda env list`
- 创建环境：
  - `conda create -n name python=3.6/2.7`(注意一定要加上 Python，指明这是Python的环境，它才会自动生成 python 解释器，否则只能得到一个空的环境，默认路径是`anaconda3/envs/环境名`)
  - 在指定路径创建新的环境：`conda create --prefix=路径\环境名 python=版本`
- 删除环境：`conda remove -n 环境名 --all`
- 启动环境：
  - Linux、Mac：`source activate 环境名`
  - Windows：`activate 环境名`
- 关闭环境:
  - Linux、Mac：`source deactivate 环境名`
  - Windows：`deactivate 环境名`

### 包管理

- 查看安装包：`conda list`
- 安装包：`conda install 包名`
- 更新包： `conda update XXX`
  - `--all`: 更新所有
  - `XXX`： 更新某包
  - `anaconda`：更新anaconda本身
- 删除包：`conda remove -n 环境名 包名`

## 编辑器配置

### 为pycharm配置Anaconda的python解释器

- 【File】-->【Settings】-->【Project: 项目名】-->【Project Interpreter】-->右上角齿轮【show all】或者【add】-->选择【Conda Environment】-->【Existing environment】-->【interpreter】选择对应环境下的`python.exe`-->【ok】
- 【File】-->【Settings】-->【Project: 项目名】-->【Project Interpreter】选择自己指定的解释器后，右上角齿轮【show all】删除没有使用的python解释器

### 为vscode配置Anaconda的python解释器

- 随便新建一个`.py`文件，点击右下角【Select Python Interpreter】，选择需要的解释器
