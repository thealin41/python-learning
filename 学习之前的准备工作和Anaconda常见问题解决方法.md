# 学习基础
理解本课程的Python实现代码之前需要以下三方面的知识和技术。
* 能够理解if语句、for语句。
* 能够自己定义类、方法（函数）。
* 会执行向量和矩阵的乘法运算。
# 开发语言 
* Python 版本根据具体情况选择，使用anaconda的时候，不需要单独安装。
* Python官网  https://www.python.org/
* search dependency by accessing https://pypi.org/search/?q=pypi
# 数据获取方法
* gdown:  https://pypi.org/project/gdown/ pip install gdown
* wget apt-get yum: The difference between wget and yum and apt-get in linux system commands  https://www.codetd.com/en/article/11071843
# Tools
* git： 安装git，并了解git原理。下载：https://git-scm.com/downloads。原理： https://git-scm.com/book/en/v2
* brew:https://brew.sh/
* Macport:   https://www.macports.org/ refer to https://www.slant.co/versus/1588/1674/~macports_vs_homebrew
* git-lfs An open source Git extension for versioning large files. https://git-lfs.github.com/. 
* curl client for url. https://curl.se/docs/ 
# 开发环境
* Anaconda 下载链接：https://www.anaconda.com/products/individual  注：Anaconda 自带Python版本
* Anaconda 安装注意事项
> * 操作系统 windows 10以上，windows 7会出现其他问题，64位机器
## 学习使用Conda
* 参考 https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html
* 管理conda，出现问题可参考 https://www.anaconda.com/blog/what-to-do-when-things-go-wrong-in-anaconda
* 管理环境
* 管理Python  ，如需要降低python版本，使用`conda install python=3.7`
* 管理依赖库  检查conda的当前环境安装了哪些库，可以使用命令  `conda list -n`， 如需检查特定环境的依赖库，可使用`conda list -n <env_name>`
以下为例子
```
conda list
# packages in environment at /Users/jane/anaconda3/envs/MLSpring:
#
# Name                    Version                   Build  Channel
addict                    2.4.0                    pypi_0    pypi
.........
torch                     1.8.1                    pypi_0    pypi
torchvision               0.11.2                   pypi_0    pypi
```
> * 确认依赖包是否正确安装， 可在conda 控制台使用
```
python 
>>> import torch
>>> from tsai.all import *
```
* 熟悉torch和torchvision适配版本矩阵，https://pypi.org/project/torchvision/
# 程序运行方法
不同的文件格式，在相应的路径和Conda环境下分别运行以下命令
## python文件 .py格式
`python <filename>.py`
## notebook文件
`ipython <filename>.ipynb`
注：如无法运行，需根据以下命令先安装ipython <br/>
`conda install ipython`
`conda install ipykernel`
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
## 使用Pip安装或者降版本
`
pip install [pkgname]==version 
`
# 常见安装问题
## 问：what's difference between pip install and conda install？
答：https://www.anaconda.com/blog/understanding-conda-and-pip
pip is a package manager.
conda is both a package manager and an environment manager.

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
pip install torch -index-url http://pypi.douban.com/simple -trusted-host pypi.douban.com
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

### 无法使用GPU
|条目|描述|备注|
|------------|----------|-----------|
|问题|can't convert CUDA tensor to numpy. Use Tensor.cpu () to copy the tensor to host memory first. ||
|原因|can't convert CUDA tensor to numpy ||
|解决方案|allocate tensor in RAM，使用.cpu()||

### torch 和torchvision不匹配
|条目|描述|备注|
|------------|----------|-----------|
|问题| ||
|原因|||
|解决方案|查看torch、torchvision和python版本的适配关系 <br/>https://github.com/pytorch/vision#installation||

### torchvision 缺乏models.util模块
|条目|描述|备注|
|------------|----------|-----------|
|问题| from torchvision.models.utils import load_state_dict_from_url 时会出现以下报错：ModuleNotFoundError: No module named 'torchvision.models.utils'||
|原因|高版本的torchvision不包括这个模块||
|解决方案|采用即可from torch.hub import load_state_dict_from_url||

### OpenCV 依赖库问题

|条目|描述|备注|
|------------|----------|-----------|
|问题| Could not build wheels for opencv-python which use PEP 517 and cannot be installed directly||
|原因|||
|解决方案|pip install --upgrade pip setuptools wheel <br/> pip install opencv-python|可参考https://stackoverflow.com/questions/63732353/error-could-not-build-wheels-for-opencv-python-which-use-pep-517-and-cannot-be|

### OpenCV 依赖库问题

|条目|描述|备注|
|------------|----------|-----------|
|问题| Could not build wheels for opencv_python, which is required to install pyproject.toml-based projects||
|原因|||
|解决方案|pip install --upgrade pip setuptools wheel <br/> pip install opencv-python||


### Conda Navigator启动失败
|条目|描述|备注|
|------------|----------|-----------|
|问题|无法启动conda navigator但可以启动conda terminal  ||
|原因|配置有问题，navigator需要升级或重置||
|解决方案|`anaconda-navigator --reset`|参考https://docs.anaconda.com/anaconda/navigator/troubleshooting/#issues-launching-or-initializing|

### 操作CVS文件出现错误
|条目|描述|备注|
|------------|----------|-----------|
|问题| “unicodedecodeerror 'utf-8' codec can't decode byte 0xff in position 0 invalid start byte”  or “keyError” ||
|原因|CVS文件编码问题||
|解决方案|注意查看CVS文件的编码格式，需要为UTF-8格式||
