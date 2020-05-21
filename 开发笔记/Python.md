# Python

## 安装-linux

- 推荐使用miniconda安装，提供成熟的虚拟环境、自动下载依赖等功能，比anaconda轻量
- 下载：可在[清华镜像网站](https://mirrors.tuna.tsinghua.edu.cn/anaconda/miniconda/)下载罪最新linux版(.sh文件)
- 安装：运行.sh文件，中途有询问则键入`yes`
- 配置环境变量：`source .bashrc`激活环境变量
- 检测：`conda -V`，显示版本

## 常用命令

- `python -V`：查看版本

## flask

## 安装

- conda install Flask

## 示例

- 代码
  
  ```python

    from flask import Flask

    app = Flask(__name__)

    # 路由
    @app.route('/hello')
    def hello_world():
        return 'Hello, World!'

    # 加上main可以用python命令执行
    if __name__ == '__main__':
        # 0.0.0.0可以让本机之外的机器访问，port指定运行的端口
        app.run(host='0.0.0.0',port=8095)
  ```
