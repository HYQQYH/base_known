### 关于安装软件
 1. ImportError: libfst.so.0: cannot open shared object file: No such file or directory
 >解决方法:<br>
 >\$whereis libfst.so.0 #查看libfst.so.0所在目录<br>
 >\$import sys<br>
 >\$sys.path #查看当前搜索目录<br>
 >\$vim ~/.bashrc  #查看bashrc脚本中是否存在此路径,若不存在,在bashrc中添加:<br>
 >`export LD_LIBRARY_PATH=/path/to/libfst.so.0:$LD_LIBRARY_PATH`<br>
 >如export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH

 2. lsb_release -a 问题：
 > vim /usr/bin/lsb_release<br>
 > change the first line to read: #! /usr/bin/python2 -Es

 4. python3.6安装pyltp下出现如下问题：
 >Failed building wheel for pyltp<br>
 >patch/include/boost/python/detail/wrap_python.hpp:50:23: fatal error: pyconfig.h: No such file or directory<br>
 >ls /usr/include/  #查看该目录发现没有python3.6，只有python2.7和python3.5<br>
 >原因是缺少python3.6的依赖，使用如下命令：<br>
 >sudo apt-get install python3.6-dev<br>
 >则ls /usr/include/下有python3.6文件夹，文件夹内有pyconfig.h文件

 5. scp 拷贝文件至远程服务器失败,可能是远程机器未安装sshd<br>
 >sudo apt-get install openssh-server

 10. 安装完openfst及pyfst后需要：
 安装openfst时make install 需要sudo权限
  export LD_LIBRARY_PATH=/usr/local/lib

 11. 在jupyter notebook中使用virtualenv:http://fosshelp.blogspot.hk/2017/08/how-to-add-python-virtualenv-to-ipython.html
 6. 安装完openfst及pyfst后需要：<br>
export LD_LIBRARY_PATH=/usr/local/lib

 7. boot分区内存不足：https://blog.csdn.net/xhw035/article/details/52422970

 8. anaconda中新建一个虚拟环境（python3.6）：`conda create -n env36 python=3.6`<br>
 > activate: `source activate env36`<br>
 > deactivate: `source deactivate`
