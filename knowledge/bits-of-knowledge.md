**base knowledge**
-------------
### 零碎知识

 1. 晓宇博客:http://jschenxiaoyu.blogspot.hk

 2. meld:在终端运行该命令,可对两个文件或两个文件夹进行对比.

 3. Gen rule:

    >`python steps/deploy/release_regex.py -l rule_raw.txt -f log -o output.txt`
 

 4. ImportError: libfst.so.1: cannot open shared object file: No such file or directory<br>
    解决方法:import sys<br>
    sys.path #查看里面是否包含/usr/local/lib<br>
    **`export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH`**
    python -c “import fst” #检查是否运行成功
  
 
 5. 一个可以看最新文章的网址:[http://www.arxiv-sanity.com](http://www.arxiv-sanity.com)

 7. 一个类实例也可以变成一个可调用对象，只需要实现一个特殊方法`__call__()`,像函数一样被调用,很多开源代码中均有体现,如nmt.
 8. os.getcwd(): 返回当前的工作目录.

 9. 查看gpu使用情况:nvidia-smi
 10. 精确率|召回率:https://www.zhihu.com/question/19645541

 11. u盘读取出错:  sudo ntfsfix /dev/sdb4

 5. Robomongo连接至服务器，在create中应设置服务器的ip地址，例如：10.12.8.18
 6. lxml: itertext():<br>
Creates a text iterator. The iterator loops over this element and all subelements, in document order, and returns all inner text.

 7. import sys<br>
sys.path.append(’引用模块的地址')

 8. http://www.json.cn/在线json解析
 9. 删除软件包：
 参考：https://www.linuxdashen.com/debianubuntu%E6%B8%85%E7%90%86%E7%A1%AC%E7%9B%98%E7%A9%BA%E9%97%B4%E7%9A%848%E4%B8%AA%E6%8A%80%E5%B7%A7
 >删除软件包：<br>
sudo apt-get remove <package-name><br>
sudo apt-get purge <package-name><br>
remove是删除软件包，purge是删除配置文件。<br>
查看系统上哪些软件包留下了残余的配置文件：<br>
dpkg -l | grep "^rc"<br>
删除这些软件包：<br>
dpkg --list | grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge<br>
删除孤儿软件包：<br>
sudo apt-get autoremove 

 10. python3绑定为python3.6:`sudo ln -s python3.6 python3`<br>

 12. 线上编辑器:https://stackedit.io/editor#<br>
 13. Finite State Transducer（FST）in NLP:https://www.douban.com/note/326761737/
 16. 从本地拷贝文件至远程
 >复制文件:`scp local_file remote_username@remote_ip:remote_folder`<br>
 >复制文件夹:`scp -r local_folder remote_username@remote_ip:remote_folder`
 
 17. 从远程拷贝文件至本地:
  >复制文件:`scp remote_username@remote_ip:remote_file local_older`<br>
 >复制文件夹:`scp -r remote_username@remote_ip:remote_folder local_folder`
 
 18. 远程拷贝带参数,如-P(端口号),-i(密匙)
 >`scp -P5837 -i aispeech.pem smy.tar.gz root@120.55.54.194:~/`<br>
 >`scp -P5837 smy.tar.gz root@47.96.190.215:~/`
