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
* 使用Conda安装 
> * 使用工具界面
> * 使用命令行
* 使用Pip安装 pip install
# 常见安装问题
## 使用pip 下载依赖包安装较慢，可采用镜像
* 方法1：参考PyPI镜像 https://developer.aliyun.com/mirror/pypi 修改 .pip/pip.conf 文件中的index-url 和trusted-host
参考镜像如下：
> * 清华大学：index-url: https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main   trusted-host: mirrors.tuna.tsinghua.edu.cn 参考链接https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/
> * 阿里云：index-url: https://mirrors.aliyun.com/pypi/simple/   trusted-host: mirrors.aliyun.com
> * 豆瓣  index-url:http://pypi.douban.com/simple trusted-host: pypi.douban.com
* 方法2：使用命令行  
`
pip install --index-url http://pypi.douban.com/simple --trusted-host pypi.douban.com --upgrade 
`
 
## 解决Python程序运行错误
* 无法启动 
|条目|描述|备注|
| ------------- | ---------- | -----------|
|问题|运行jupyter notebook出现白屏||
|原因|浏览器不支持notebook||
|解决方案|更换为谷歌浏览器||
* 
|条目|描述|备注|
| ------------- | ---------- | -----------|
|问题|’tqdm_notebook’ object has no attribute 'disp’||
|原因|缺少ipywidgets||
|解决方案|pip install ipywidgets||

*
|条目|描述|备注|
| ------------- | ---------- | -----------|
|问题|Can't pickle <function <lambda> at 0x7f989a4e10d0>: attribute lookup <lambda> on __main__ failed||

|原因|||
|解决方案|||