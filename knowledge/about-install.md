### 关于安装软件

 1. 从源文件安装python3.6:
 >参考链接:http://blog.csdn.net/jeryjeryjery/article/details/77880227
 >1.安装openSSL:
 >\$sudo apt-get install openssl
\$sudo apt-get install libssl-dev
2./usr/bin/lsb_release文件中的#!/usr/bin/python3 -Es 改为 #!/usr/bin/python2.7 -Es
\$cd Python-3.6.2
\$./configure --with-ssl
\$sudo make
$sudo make altinstall

 2. ImportError: libfst.so.0: cannot open shared object file: No such file or directory
 >解决方法:
 >\$whereis libfst.so.0 #查看libfst.so.0所在目录
 >\$import sys
 >\$sys.path #查看当前搜索目录
 >\$vim ~/.bashrc  #查看bashrc脚本中是否存在此路径,若不存在,在bashrc中添加:
 >`export LD_LIBRARY_PATH=/path/to/libfst.so.0:$LD_LIBRARY_PATH`
 >如export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH

 3. ModuleNotFoundError: No module named 'softwareproperties'
 >sudo vim /usr/bin/add-apt-repository
 >Change package header from `python3` to `python3.4` (or lower)
 >适用ubuntu14.04

 4. 问题：使用apt-get -f install后出现各种问题，如：
 >有 15 个软件包没有被完全安装或卸载。
解压缩后会消耗掉 0 B 的额外空间。
正在设置 python2.7-minimal (2.7.6-5) ...
\# Empty sitecustomize.py to avoid a dangling symlink
dpkg-query: error: --listfiles needs a valid package name but 'libpython2.7-minimal' is not: ambiguous package name 'libpython2.7-minimal' with more than one installed instance
使用 --help 查看关于查询软件包的帮助。
dpkg: error processing package python2.7-minimal (--configure):
子进程 已安装 post-installation 脚本 返回了错误号 1
dpkg: dependency problems prevent configuration of python-minimal:
python-minimal 依赖于 python2.7-minimal (>= 2.7.5-1~)；然而：
软件包 python2.7-minimal 尚未配置。
dpkg: error processing package python-minimal (--configure):
依赖关系问题 - 仍未被配置
dpkg: dependency problems prevent configuration of python2.7:
python2.7 依赖于 python2.7-minimal (= 2.7.6-5)；然而：
软件包 python2.7-minimal 尚未配置。
dpkg: error processing package python2.7 (--configure):
依赖关系问题 - 仍未被配置
dpkg: dependency problems prevent configuration of python:
python 依赖于 python2.7 (>= 2.7.5-1~)；然而：
软件包 python2.7 尚未配置。
python 依赖于 python-minimal (= 2.7.5-5)；然而：
软件包 python-minimal 尚未配置。
dpkg: error processing package python (--configure):
依赖关系问题 - 仍未被配置
dpkg: dependency problems prevent configuration of python-gi:
python-gi 依赖于 python (>= 2.7)；然而：
软件包 python 尚未配置。
python-gi 依赖于 python (<< 2.8)；然而：
软件包 python 尚未配置。
dpkg: error processing package python-gi (--configure):
依赖关系问题 - 仍未被配置
dpkg: dependency problems prevent configuration of python-apt:
python-apt 依赖于 python (>= 2.7)；然而：
软件包 python 尚未配置。
python-apt 依赖于 python (<< 2.8)；然而：
软件包 python 尚未配置。
dpkg: error processing package python-apt (--configure):
依赖关系问题 - 仍未被配置
dpkg: dependency problems prevent configuration of gconf2:
gconf2 依赖于 python；然而：
软件包 python 尚未配置。
dpkg: error processing package gconf2 (--configure):
依赖关系问题 - 仍未被配置
dpkg: dependency problems prevent configuration of python-six:
python-six 依赖于 python (>= 2.7)；然而：
软件包 python 尚未配置。
python-six 依赖于 python (<< 2.8)；然而：
软件包 python 尚未配置。
dpkg: error processing package python-six (--configure):
依赖关系问题 - 仍未被配置
dpkg: dependency problems prevent configuration of python-chardet:
python-chardet 依赖于 python2.6 | python2.7；然而：
未安装软件包 python2.6。
软件包 python2.7 尚未配置。
python-chardet 依赖于 python (>= 2.6.6-7~)；然而：
软件包 python 尚未配置。
python-chardet 依赖于 python (<< 2.8)；然而：
软件包 python 尚未配置。
dpkg: error processing package python-chardet (--configure):
依赖关系问题 - 仍未被配置
dpkg: dependency problems prevent configuration of python-debian:
python-debian 依赖于 python (>= 2.6.6-7~)；然而：
软件包 python 尚未配置。
python-debian 依赖于 python (<< 2.8)；然而：
软件包 python 尚未配置。
python-debian 依赖于 python-six；然而：
软件包 python-six 尚未配置。
python-debian 依赖于 python-chardet；然而：
软件包 python-chardet 尚未配置。
dpkg: error processing package python-debian (--configure):
依赖关系问题 - 仍未被配置
dpkg: dependency problems prevent configuration of gdebi-core:
gdebi-core 依赖于 python:any (>= 2.6.6-7~)；然而：
软件包 python 尚未配置。
gdebi-core 依赖于 python-apt (>= 0.7.97)；然而：
软件包 python-apt 尚未配置。
gdebi-core 依赖于 python-debian (>= 0.1.15)；然而：
软件包 python-debian 尚未配置。
dpkg: error processing package gdebi-core (--configure):
依赖关系问题 - 仍未被配置
dpkg: dependency problems prevent configuration of libgksu2-0:
libgksu2-0 依赖于 gconf2 (>= 2.28.1-2)；然而：
软件包 gconf2 尚未配置。
dpkg: error processing package libgksu2-0 (--configure):
依赖关系问题 - 仍未被配置
dpkg: dependency problems prevent configuration of gksu:
gksu 依赖于 libgksu2-0 (>= 2.0.8)；然而：
软件包 libgksu2-0 尚未配置。
dpkg: error processing package gksu (--configure):
依赖关系问题 - 仍未被配置
dpkg: dependency problems prevent configuration of gdebi:
gdebi 依赖于 python:any (>= 2.6.6-7~)；然而：
软件包 python 尚未配置。
gdebi 依赖于 gdebi-core (= 0.9.3)；然而：
软件包 gdebi-core 尚未配置。
gdebi 依赖于 python-gi；然而：
软件包 python-gi 尚未配置。
gdebi 依赖于 gksu；然而：
软件包 gksu 尚未配置。
dpkg: error processing package gdebi (--configure):
依赖关系问题 - 仍未被配置
dpkg: dependency problems prevent configuration of lsb-release:
lsb-release 依赖于 python (>= 2.7)；然而：
软件包 python 尚未配置。
lsb-release 依赖于 python (<< 2.8)；然而：
软件包 python 尚未配置。
dpkg: error processing package lsb-release (--configure):
依赖关系问题 - 仍未被配置
在处理时有错误发生：
python2.7-minimal
python-minimal
python2.7
python
python-gi
python-apt
gconf2
python-six
python-chardet
python-debian
gdebi-core
libgksu2-0
gksu
gdebi
lsb-release
E: Sub-process /usr/bin/dpkg returned an error code (1)
解决方法：
cd /var/lib/dpkg 
sudo mv info info.bak 
sudo mkdir info
sudo apt-get autoremove #记得执行了此操作
疑似原因:更新bazel时运行sudo apt-get upgrade bazel出错，接着http://www.cnblogs.com/Climbing-Snail/p/6670057.html按这网页方式，运行sudo apt-get -f install bazel后出现以上错误。
-f是忽略依赖，依赖不解决的应用很可能用不了的，如果是要想不安装推荐应用的话应该用apt-get --no-install-recommends install

 5. lsb_release -a 问题：
 > vim /usr/bin/lsb_release
 > change the first line to read: #! /usr/bin/python2 -Es

