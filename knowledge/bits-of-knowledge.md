**base knowledge**
-------------
### 零碎知识

 1. meld:在终端运行该命令,可对两个文件或两个文件夹进行对比.

 2. Gen rule:

 `python steps/deploy/release_regex.py -l rule_raw.txt -f log -o output.txt`
 

 3. ImportError: libfst.so.1: cannot open shared object file: No such file or directory
解决方法:import sys
sys.path #查看里面是否包含/usr/local/lib

    **export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH**

    python -c “import fst” #检查是否运行成功
  
 
 8. 一个可以看最新文章的网址:[http://www.arxiv-sanity.com](http://www.arxiv-sanity.com)
 9. 关于无偏估计的解释:
比如我要对某个学校一个年级的上千个学生估计他们的平均水平（真实值，上帝才知道的数字），那么我决定抽样来计算。
我抽出一个10个人的样本，可以计算出一个均值。那么如果我下次重新抽样，抽到的10个人可能就不一样了，那么这个从样本里面计算出来的均值可能就变了，对不对？
因为这个均值是随着我抽样变化的，而我抽出哪10个人来计算这个数字是随机的，那么这个均值也是随机的。但是这个均值也会服从一个规律（一个分布），那就是如果我抽很多次样本，计算出很多个这样的均值，这么多均值们的平均数应该接近上帝才知道的真实平均水平。
如果你能理解**“样本均值”**其实也是一个**随机变量**，那么就可以理解为这个**随机变量的期望是真实值**，所以无偏（这是无偏的定义）；**而它又是一个随机变量，只是估计而不精确地等于，所以是无偏估计量。**

 10. 一个类实例也可以变成一个可调用对象，只需要实现一个特殊方法`__call__()`,像函数一样被调用,很多开源代码中均有体现,如nmt.
 13. os.getcwd(): 返回当前的工作目录.

 15. 查看gpu使用情况:nvidia-smi
 16. 精确率|召回率:https://www.zhihu.com/question/19645541

 17. u盘读取出错:  sudo ntfsfix /dev/sdb4

  
 20. 如果需要登录服务器，使用如下命令：
>ssh tianjin
>如果需要传文件，使用如下命令：
>scp tianjin:/path/filename /localpath/
>以上两条命令都需要输入跳板机的密钥密码

 21. 虚拟环境下安装python 3.5：
>首先安装virtualenvwrapper，可以选择apt安装或者pip安装
apt安装
\$ sudo apt-get install virtualenvwrapper
pip安装
\$ sudo pip install virtualenvwrapper
当你需要使用Python2开发项目时，建立一个Python2的虚拟环境：
\$ mkvirtualenv -p /usr/bin/python2 env27
当你需要Python3开发时：
\$ mkvirtualenv -p /usr/bin/python3.4 env34
然后可以随时切换不同的虚拟环境：
\$ workon env27  # 进入Python2环境
\$ workon env34  # 进入Python3环境


 27. random.shuffle的函数原型为：random.shuffle(x[, random])，用于将一个列表中的元素打乱。
random.choice从序列中获取一个随机元素。其函数原型为：random.choice(sequence)。参数sequence表示一个有序类型。

 28. json.dumps是将一个Python数据类型列表进行json格式的编码解析.
解码python json格式，可以用这个模块的json.loads()函数的解析方法

 34. Robomongo连接至服务器，在create中应设置服务器的ip地址，例如：10.12.8.18
 35. lxml: itertext():
Creates a text iterator. The iterator loops over this element and all subelements, in document order, and returns all inner text.

 36. import sys
sys.path.append(’引用模块的地址')

 39. http://www.json.cn/在线json解析
 40. 删除软件包：
 参考：https://www.linuxdashen.com/debianubuntu%E6%B8%85%E7%90%86%E7%A1%AC%E7%9B%98%E7%A9%BA%E9%97%B4%E7%9A%848%E4%B8%AA%E6%8A%80%E5%B7%A7
 >删除软件包：
sudo apt-get remove <package-name>
sudo apt-get purge <package-name>
remove是删除软件包，purge是删除配置文件。
查看系统上哪些软件包留下了残余的配置文件：
dpkg -l | grep "^rc"
删除这些软件包：
dpkg --list | grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
删除孤儿软件包：
sudo apt-get autoremove 

 43. python3绑定为python3.6:`sudo ln -s python3.6 python3`

