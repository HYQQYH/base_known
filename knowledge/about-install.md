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