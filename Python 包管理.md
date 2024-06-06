启用pip
一般不用手动启用pip。当系统提示 No module named pip，需要启用pip
python -m ensure pip

配置清华源[1]
用于提升在大陆地区安装Python库的速度
升级pip到最新版本
python -m pip install --upgrade pip
配置默认使用清华源
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple

使用pip 安装Python依赖

例如，安装用于数学计算的库Numpy[2]
pip install numpy
更新Python依赖（不是必要的）
更新单个库
pip install --upgrade xxx
例如更新Numpy
pip install --upgrade numpy

更新所有库
需要先安装一个第三方库
pip install pip-review
然后使用第三方库，批量更新已安装的Python库
pip-review --interactive

输入A，则表示更新所有的库。


卸载库
卸载单个库
使用pip uninstall xxx卸载特定的库，例如卸载numpy
pip uninstall numpy

如果出现“拒绝访问xx"的报错，可以使用“以管理员身份运行”cmd界面。
卸载所有库
需要创建python脚本，例如命名为uninstall_libs.py，以管理员身份进入cmd界面，切换到脚本uninstall_libs.py所在的目录，执行 python uninstall_libs.py

import pkg_resources
import subprocess

dists = [d for d in pkg_resources.working_set]
for dist in dists:
subprocess.call("pip uninstall -y " + dist.key, shell=True)





参考链接
[1] https://mirrors.tuna.tsinghua.edu.cn/help/pypi/
[2] https://numpy.org/

注意
[1]本教程适用于Windows10、11 ，Linux 版本不适用。Linux中，根据实际情况使用pip3 替代pip，使用python3 替代python. Ubuntu 24.04或者更高版本，可能需要使用sudo  apt install python3-xxx来安装python 的第三方库。
