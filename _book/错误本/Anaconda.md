# Anaconda

## jupyter不支持中文和负号显示

- 原因：未知
- 解决：
  - `mpl.rcParams['font.sans-serif'] = ['SimHei']`，指定默认字体
  - `mpl.rcParams['axes.unicode_minus'] = False`，解决保存图像是负号'-'显示为方块的问题

- jupyter安装包需要注意
  - 注意：数据分析jupyter notebook默认使用`base`环境
  - 打开 `anacodna prompt`，`pip install pymysql` 安装

## import flask报错ImportError: DLL load failed: 找不到指定的模块

- 原因：pycharm解释器环境变量没配置好
- 解决：先用命令`python XX.py`来运行文件

## pycharm的连接不上console

- [参考](https://stackoverflow.com/questions/54175042/python-3-7-anaconda-environment-import-ssl-dll-load-fail-error)
- 原因：没有为pycharm添加环境变量
- 解决： 命令行输入`echo %PATH%`得到环境变量，然后pycharm -->setting-->Build, Execution, Deployment -> Console -> Python Console -> 右侧的Environment variables添加环境变量，变量名是`PATH`，值是`echo %PATH%`得到的环境变量
