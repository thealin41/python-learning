# 开发语言
* Python 版本根据具体情况选择，使用anaconda的时候，不需要单独安装。
* Python官网  https://www.python.org/
# 开发环境
* Anaconda 下载链接：https://www.anaconda.com/products/individual  注：Anaconda 自带Python版本
* Anaconda 安装注意事项
> * 操作系统 windows 10以上，windows 7会出现其他问题，64位机器

* 学习使用Conda，https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html
> * 管理conda
> * 管理环境
> * 管理Python
> * 管理依赖库

# 常见安装库方法
## 使用Conda安装 
* 使用工具界面
* 使用命令行
`
conda create --name [envname] python=3.8  
`
* 检查当前环境的安装包
`
pip list
`
## 使用Pip安装
`
pip install [pkgname]==version
`
# 常见安装问题
## 问：为何要建立不同的Python环境？
答：Python项目依赖于大量的包，不同的项目依赖的包版本不一样。为避免出现依赖包相关的问题，可使用Conda为每个项目创建独立的环境，包含文件、包和他们的依赖关系，这些环境不会与其他环境发生交互。通常将依赖包文件和版本信息放在requirements文件中，建立环境时，只需要执行`pip install -r requirements.txt`。当开始使用Conda时，你已经有了一个名为base的默认环境。不过，不建议把程序放到基础环境中，而是需要创建独立的环境来保持程序相互隔离。
可参考 https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html#managing-environments
## 问：如何修改jupyter notebook 文件的位置？
答：默认在C盘，可修改位置
在jupyter_notebook_config.py 文件中修改
`
c.NotebookApp.notebook_dir = 'D:/workspace/jupyter'
`
注：如无jupyter_notebook_config.py，打开Anaconda Prompt输jupyter notebook
–generate-config，自动生成一个.jupyter的文件夹，路径为 C:\Users\[username]\.jupyter
## 问：使用pip 下载依赖包安装较慢，如何解决？
答：可采用镜像
### 方法1：参考PyPI镜像 https://developer.aliyun.com/mirror/pypi 修改 .pip/pip.conf 文件中的index-url 和trusted-host
以下为pip文件放置路径，如果无此文件，可自行创建。
[windows环境]文件名后缀为ini，即pip.ini
路径为：C:\Users（用户）\janey（当前用户）\pip
[MacOS]文件名后缀为conf,即pip.conf
/User(用户)/jane(用户名)
参考镜像如下：
* 清华大学：index-url: https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main   trusted-host: mirrors.tuna.tsinghua.edu.cn 参考链接https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/
* 阿里云：index-url: https://mirrors.aliyun.com/pypi/simple/   trusted-host: mirrors.aliyun.com
* 豆瓣  index-url:http://pypi.douban.com/simple trusted-host: pypi.douban.com
以下为一个案例
```
```
### 方法2：在Conda环境下使用命令行  
```
pip install [modulename]
pip install -r requirements.txt
pip install torch -index-url http://pypi.douban.com/simple -trusted-host pypi.douban.com`
```
 
## 解决Python程序运行错误
### 无法启动 
|条目|描述|备注|
|------------- |----------| -----------|
|问题|运行jupyter notebook出现白屏||
|原因|浏览器不支持notebook||
|解决方案|将系统默认浏览器设置为谷歌浏览器，即可看到|在控制面板即可设置|

### 缺少进程条支持库
|条目|描述|备注|
|------------- |----------| -----------|
|问题|’tqdm_notebook’ object has no attribute 'disp’||
|原因|缺少ipywidgets|ipywidgets是支持显示进度条的|
|解决方案|pip install ipywidgets||

### 运行程序中出现错误
|条目|描述|备注|
|------------|----------|-----------|
|问题|Can't pickle <function <lambda> at 0x7f989a4e10d0>: attribute lookup <lambda> on __main__ failed||
|原因|所用浏览器不适合程序运行||
|解决方案|将系统默认浏览器设置为谷歌浏览器，即可正常运行程序||