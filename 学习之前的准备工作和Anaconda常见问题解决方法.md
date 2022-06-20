# 学习基础
理解本课程的Python实现代码之前需要以下三方面的知识和技术。
1）能够理解if语句、for语句。
2）能够自己定义方法（函数）。
3）会执行向量和矩阵的乘法运算。
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
> * 管理依赖库  检查conda的当前环境安装了哪些库，可以使用命令  `conda list`
# 程序运行方法
不同的文件格式，在相应的路径和Conda环境下分别运行以下命令
## python文件 .py格式
`python <filename>.py`
## notebook文件
`ipython <filename>.ipynb`
注：如无法运行，需根据以下命令先安装ipython
`conda install ipython`

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
## 问：如何为不同的Python环境安装相应的jupyter notebook？
答：在Python环境终端，运行
`conda install jupyter`
安装成功后，要打开jupyter notebook 文件，可在anaconda界面上点击“open with Jupyter Notebook”，也可以使用命令
`jupyter notebook`
## 问：如何修改jupyter notebook 文件的路径？
答：可采用以下几种方法修改路径。
1. jupyter notebook 默认的默认路径为  C:\Users\  [username]，可修改其路径
在jupyter_notebook_config.py 文件中修改
`
c.NotebookApp.notebook_dir = 'D:\\workspace\\jupyter'
`
参考链接 https://jupyter-notebook.readthedocs.io/en/stable/public_server.html
注：如无jupyter_notebook_config.py，打开Anaconda Prompt输jupyter notebook
–generate-config，自动生成一个.jupyter的文件夹，路径为 C:\Users\[username]\.jupyter
2. 可使用命令行 jupyter notebook --notebook-dir=D:\workspace\jupyter
如图所示  ![设置路径](https://github.com/bettermorn/IAICourse/blob/main/img/%E8%AE%BE%E7%BD%AEjupyternotebook%E4%BD%8D%E7%BD%AE%E5%91%BD%E4%BB%A4.png)
图片链接为https://github.com/bettermorn/IAICourse/blob/main/img/%E8%AE%BE%E7%BD%AEjupyternotebook%E4%BD%8D%E7%BD%AE%E5%91%BD%E4%BB%A4.png
再使用 Anaconda Jupyter Notebook 命令打开，可跳转到设置的路径。
3. 使用DOS命令切换到相应目录，再运行命令启动 notebook，如下
`
jupyter notebook
`
如图所示
![在环境控制台启动](https://github.com/bettermorn/IAICourse/blob/main/img/%E4%BB%8Enotebook%E6%96%87%E4%BB%B6%E8%B7%AF%E5%BE%84%E4%B8%AD%E5%90%AF%E5%8A%A8notebook.png)
图片链接为 https://github.com/bettermorn/IAICourse/blob/main/img/%E4%BB%8Enotebook%E6%96%87%E4%BB%B6%E8%B7%AF%E5%BE%84%E4%B8%AD%E5%90%AF%E5%8A%A8notebook.png
## 问：使用pip 下载依赖包安装较慢，如何解决？
答：可采用镜像
### 方法1：参考PyPI镜像 https://developer.aliyun.com/mirror/pypi 修改 .pip/pip.conf 文件中的index-url 和trusted-host
* 以下为pip文件放置路径，如果无此文件，可自行创建。
> * [windows环境]文件名后缀为ini，即pip.ini  路径为：C:\Users（用户）\janey（当前用户）\pip
> * [MacOS]文件名后缀为conf,即pip.conf   路径为：/User(用户)/jane(用户名)
* 参考镜像如下：
> * 清华大学：index-url: https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main   trusted-host: mirrors.tuna.tsinghua.edu.cn 参考链接https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/
> * 阿里云：index-url: https://mirrors.aliyun.com/pypi/simple/   trusted-host: mirrors.aliyun.com
> * 豆瓣  index-url:http://pypi.douban.com/simple trusted-host: pypi.douban.com
* 以下为一个案例
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

### 权限不够导致symbolic link privilege错误
|条目|描述|备注|
|------------|----------|-----------|
|问题|Windows下出现ERROR: Command errored out with exit status 1: OSError: symbolic link privilege not held||
|原因|权限不够|参考：https://github.com/explosion/spaCy/issues/895|
|解决方案|以管理员身份启动Anaconda Navigator||

### 无法编译依赖包
|条目|描述|备注|
|------------|----------|-----------|
|问题|Failed building wheel for hydra||
|原因|error: Microsoft Visual C++ 14.0 or greater is required. |升级VC Builder|
|解决方案|安装Microsoft C++ Build Tools: https://visualstudio.microsoft.com/visual-cpp-build-tools/||
