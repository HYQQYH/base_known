**base knowledge**
-------------
### 关于正则表达式:

 1. 正则表达式,(?<=...)之前的字符串需要匹配表达式才能成功匹配.不消耗字符串内容.
正则表达式,(?=...)之后的字符串需要匹配表达式才能成功匹配.不消耗字符串内容.
>如:`pattern = re.compile(r'(?<=[>"])test(?=[<"])')`
这正则表示当test字符串左右两边均为`[>"]`中的其中一个字符时才能匹配成功.

 2. 正则表达式,`(?<!...)`之前的字符串需要不匹配表达式才能成功匹配.不消耗字符串内容.
正则表达式,`(?!...)`之后的字符串需要不匹配表达式才能成功匹配.不消耗字符串内容.

 3. 匹配形如”///abc”的字符串,要求只按最后一个/进行split
  

    b = re.split(‘/(?!/)’,a)
    

 4. `re.IGNORECASE`
让正则表达式忽略大小写，这样一来，[A-Z]也可以匹配小写字母了。
    re.DOTALL
影响'.'的行为，平时'.'匹配除换行符以外的所有字符，指定了本标志以后，也可以匹配换行符。

 5. List item

### 零碎知识

 1. meld:在终端运行该命令,可对两个文件或两个文件夹进行对比.

 2. Gen rule:

 `python steps/deploy/release_regex.py -l /home/aisp/hyq/HIS/KGQA/examples/data/AI_industry/rules/regex/rule_raw -f /home/aisp/hyq/HIS/genrule-byclass/temp -o /home/aisp/hyq/HIS/KGQA/examples/data/AI_industry/rules/regex/all-rule`
 

 3. ImportError: libfst.so.1: cannot open shared object file: No such file or directory
解决方法:import sys
sys.path #查看里面是否包含/usr/local/lib

    **export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH**

    python -c “import fst” #检查是否运行成功
  

 4. ls -lt:按时间排序.
 5. 网页端flask打开方式:
 >1.先启动flask_http_service/flask_app.py 5000
   2.再启动flask_web_client/flask_app.py 5001
注:1.中的flask调用engine中的client.py查询数据库 2.中的flask调用1中的结果.

 6. 另一种测试方式,启动flask_app.py后,使用curl命令在另一新开终端中发送命令.
 >`curl -i -H "Content-Type:application/json" -X POST -d '{"query":"hinton发表的文章"}' http://10.10.111.250:5000/graph/query`
 如果启动的是本地的服务器,后面的地址应改为相对应的地址,如:
curl -i -H "Content-Type:application/json" -X POST -d '{"query":"hinton发表的文章"}' http://0.0.0.0:5000/graph/query

 7. 单元测试运行方式:`python3 -m pytest -s tests/test_engine.py` #-s参数可以在终端中看到test输出
 8. 一个可以看最新文章的网址:[http://www.arxiv-sanity.com](http://www.arxiv-sanity.com)
 9. 关于无偏估计的解释:
比如我要对某个学校一个年级的上千个学生估计他们的平均水平（真实值，上帝才知道的数字），那么我决定抽样来计算。
我抽出一个10个人的样本，可以计算出一个均值。那么如果我下次重新抽样，抽到的10个人可能就不一样了，那么这个从样本里面计算出来的均值可能就变了，对不对？
因为这个均值是随着我抽样变化的，而我抽出哪10个人来计算这个数字是随机的，那么这个均值也是随机的。但是这个均值也会服从一个规律（一个分布），那就是如果我抽很多次样本，计算出很多个这样的均值，这么多均值们的平均数应该接近上帝才知道的真实平均水平。
如果你能理解**“样本均值”**其实也是一个**随机变量**，那么就可以理解为这个**随机变量的期望是真实值**，所以无偏（这是无偏的定义）；**而它又是一个随机变量，只是估计而不精确地等于，所以是无偏估计量。**

 10. 一个类实例也可以变成一个可调用对象，只需要实现一个特殊方法`__call__()`,像函数一样被调用,很多开源代码中均有体现,如nmt.
 11. 提取recodeId:
`grep '"core": "/data/chat"' log/$yesterday.log | grep -o -P '"recordId": ".*?"' | awk -F ': ' '{print $2}' | sed 's/"//g' > recordId/$yesterday.recordId`
 

 12. 按第2列对文件内容进行排序,分隔符为tab: 
 `sort -n -k 2 -t \t test.txt -o test.txt`
 -o命令表示将排序后的内容存储于原文件中.
 

 13. os.getcwd(): 返回当前的工作目录.

 14. 使用awk命令对文件内容进行洗牌:
   

     awk 'BEGIN{srand()}{b[rand()NR]=$0}END{for(x in b)print b[x]}' test_result1 >> test

 15. 查看gpu使用情况:nvidia-smi
 16. 准确率|召回率|F值
 准确率 = 提取出的正确信息条数 / 提取出的信息条数  =======> 查准率
召回率 = 提取出的正确信息条数 / 样本中的信息条数 =======> 查全率
F值  = 正确率 * 召回率 * 2 / (正确率 + 召回率)

 17. u盘读取出错:  sudo ntfsfix /dev/sdb4
 18. 使用sed命令行去掉 <200b>
  `sed -i 's/\xe2\x80\x8b//g' inputfile`
  

 19. 去除重复行
 

    :g/^\(.*\)\$\n\1$/d                      //去除重复行

 shell脚本中去重:`sort -u input-file -o output-file`
 

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
 

 22. gf可打开光标下的路径，ctrl+o可退回之前页面
:tabnew[file]，在tab页中编辑打开文件，gt进行页面切换
shift + #:查找光标所在字符串

 23. 去掉vim 中的^M符号
 >：%s/^M//g
tr -d "\015" <douban_que_ans2> douban_que_ans3

 24. `grep -o 'div class=' tieba.htm | wc -l` 输出查找到的div class=的数目

 25. `grep -n http://tieba.baidu.com/f?kw=%E5%91%A8%E6%9D%B0%E4%BC%A6 spider-tieba_2017-05-05-09:02:39.log | grep -o '\[http.*\]' | sort -u`
 26. `grep -P -o '<a href.*?class="j_th_tit ".*?</a>' tieba.html` 结果如下：
`<a href="/p/5089096303" title="`【JayCn】【地表最强】" target="_blank" class="j_th_tit ">【JayCn】【地表最强】`</a>`

 27. random.shuffle的函数原型为：random.shuffle(x[, random])，用于将一个列表中的元素打乱。
random.choice从序列中获取一个随机元素。其函数原型为：random.choice(sequence)。参数sequence表示一个有序类型。

 28. json.dumps是将一个Python数据类型列表进行json格式的编码解析.
解码python json格式，可以用这个模块的json.loads()函数的解析方法

 29. 终端命令：`Shift+Ctrl+T` 打开新的标签页
`ctrl + pageUp ctrl + pageDown`可在多个屏幕中进行切换

 30. `python tiebacontentParser.py | tee tieba.htm`,查看爬取的htm页面，tee指令会从标准输入设备读取数据，将其内容输出到标准输出设备，同时保存成文件。
 31. yw //复制从光标开始到词尾的字符。ndw或ndW：删除光标处开始及其后的n-1个字
 32. grep 'failed to parse' log/spider-shiwanwhy_2017-04-24-11:14:22.log | awk -F 'with parser' '{print $2}' | sort -u
 33. du -sh pages:查看文件大小。
wc -l pages：查看文件数量

 34. Robomongo连接至服务器，在create中应设置服务器的ip地址，例如：10.12.8.18
 35. lxml: itertext():
Creates a text iterator. The iterator loops over this element and all subelements, in document order, and returns all inner text.

 36. import sys
sys.path.append(’引用模块的地址')

 37. 日志logging模块：http://www.cnblogs.com/dkblog/archive/2011/08/26/2155018.html
 38. sys.argv[]是用来获取命令行参数的，sys.argv[0]表示代码本身文件路径，所以参数从1开始。
 39. http://www.json.cn/在线json解析

### Git知识

 1. Git push冲突的解决方法:(both modified)
 > 1.`git add xxx`
2.`git commit -m xx`
3.`git push  #! [rejected]        master -> master (fetch first)`
4.`git pull –rebase`
5.`git rebase –continue # examples/data/AI_industry/rules/rules.txt: needs merge,You must edit all merge conflicts and then mark them as resolved using git add`
6.`#merge file`
7.`git rebase –continue`
8.` if 7 fail: git rebase pull –rebase then 7`

 2. 从git里将jieba引入到服务器：
git clone https://github.com/fxsjy/jieba
mv jieba/ jieba_t
cp jieba_t/jieba jieba -r

 3. 
 4. 

### Vim知识

 1. vim中从第n行开始到到最后一行进行替换
 `:n,$s/vivian/sky/g`带g表示替换所有,不带只替换第一个
复制多行,`:10,20 co 21`, 表示复制第10行到第20行,并放到21行
 2. vim 查找字符串出现的次数
 在所有行中查找 字符串 出现的次数
`:%s/字符串/&/gn`
在m和n行之间查找 字符串 出现的次数
`:m,ns/字符串/&/gn`
 3. vim注释多行方法：1、进入vi/vim编辑器，按CTRL+V进入可视化模式（VISUAL BLOCK）。2、移动光标上移或者下移，选中多行的开头。3、选择完毕后，按大写的的I键，此时下方会提示进入“insert”模式，输入你要插入的注释符，最后按ESC键，多行代码被注释
 4. :nohl, 取消vim中搜索高亮显示
 5. vim编辑快捷键：
 >复制一行：yy
粘贴：p
删除一个单词：dw， 删除一个单词并进入插入模式：cw
删除一行：dd, 删除后进入插入模式用cc或者S
撤销：u
删除到行尾：D或C

 6. List item

### 数据库相关

 1. Mogo查询:`db.getCollection('newlog').find({'message.core': /chat/})`

### tensorflow 相关

 1. tensorflow中限制任务占用显存大小方法:
>1.按比例预留:
tf_config = tensorflow.ConfigProto()
tf_config.gpu_options.per_process_gpu_memory_fraction = 0.5 # 分配50%
session = tensorflow.Session(config=tf_config)
2.自适应然后自动增长
tf_config = tensorflow.ConfigProto()
tf_config.gpu_options.allow_growth = True # 自适应
session = tensorflow.Session(config=tf_config)

 2. tensorflow中使用gpu时,可以在session中加选项,如:
 `with tf.Session(config=tf.ConfigProto(allow_soft_placement=True, log_device_placement=True))`
其中 allow_soft_placement能让tensorflow遇到无法用GPU跑的数据时,自动切换成CPU进行. log_device_placement则记录一些日志.

 3. 关于集群中安装tensorflow:
 >3.1.集群中已经装好`python-pip python-dev python-virtualenv`等环境,只需下载`virtualenv`的二进制文件,通过运行`python virtualenv-15.1.0/virtualenv.py –system-site-packages env`继承系统的环境.
3.2.启动虚拟环境,`source env/bin/activate`
进入虚拟交互环境.
3.3.运行`pip install –upgrade tensorflow-gpu`
若第3步出错,(资源请求错误),转4
3.4.`pip install –upgrade https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow_gpu-1.2.1-cp27-none-linux_x86_64.whl`
3.5.不用时,关闭虚拟环境,`deactivate`
注:集群中已经安装过`cuda`,需将`cuda`目录加入`~/.bashrc`文件中,将如下代码加入:
    export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/lib64
之后,`source ~/.bashrc`

 >其中遇到的bug记录如下(安装完后运行出错):
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/aifs/users/xyc43/env/lib/python2.7/site-packages/tensorflow/__init__.py", line 24, in <module>
    from tensorflow.python import *
  File "/aifs/users/xyc43/env/lib/python2.7/site-packages/tensorflow/python/__init__.py", line 49, in <module>
    from tensorflow.python import pywrap_tensorflow
  File "/aifs/users/xyc43/env/lib/python2.7/site-packages/tensorflow/python/pywrap_tensorflow.py", line 52, in <module>
    raise ImportError(msg)
ImportError: Traceback (most recent call last):
  File "/aifs/users/xyc43/env/lib/python2.7/site-packages/tensorflow/python/pywrap_tensorflow.py", line 41, in <module>
    from tensorflow.python.pywrap_tensorflow_internal import *
  File "/aifs/users/xyc43/env/lib/python2.7/site-packages/tensorflow/python/pywrap_tensorflow_internal.py", line 28, in <module>
    _pywrap_tensorflow_internal = swig_import_helper()
  File "/aifs/users/xyc43/env/lib/python2.7/site-packages/tensorflow/python/pywrap_tensorflow_internal.py", line 24, in swig_import_helper
    _mod = imp.load_module('_pywrap_tensorflow_internal', fp, pathname, description)
ImportError: libcusolver.so.8.0: cannot open shared object file: No such file or directory
Failed to load the native TensorFlow runtime.
See https://www.tensorflow.org/install/install_sources#common_installation_problems
for some common reasons and solutions.  Include the entire stack trace
above this error message when asking for help.
解决方法:将cuda路径加入~/.bashrc中

 4. tensorboard可视化： 
>python ~/.local/lib/python2.7/site-packages/tensorflow/tensorboard/tensorboard.py --logdir="./graphs" --port 6006
或者：tensorboard --logdir="./graphs" --port 6006
http://localhost:6006/

 5. List item

### Docker相关

 1. 创建Dockerfile
 2. 使用 Dockerfile 文件，通过 docker build 命令来构建一个镜像。

     >docker build -t runoob/centos:6.7 .
     >-t:指定要创建的目标镜像名
     . ：Dockerfile 文件所在目录，可以指定Dockerfile 的绝对路径
     
 3. `docker run -p 6001:50001 -t -i hyq/kgqa:1.2`
 > 50001端口为dockerfile中指定http服务器的端口,使用-p命令,将其映射至本机的6001端口,并修改flask_web.py中的默认端口号,使之与6001对应.运行时,另制定flask_web.py端口号,如7001,即可成功运行.

 4. 使用命令:`docker exec $IMAGE_ID ls` 可以查看该docker中的目录.
 5. 使用命令:`docker exec $IMAGE_ID cat engine.log` 可查看docker服务器中的log.
 6.  `docker image rm -f IMAGEID`删除docker image


### 项目相关

 1. flask中,从外部传参给函数内部:
 

    >from flask import app
    app.config['engine'] = KGQAEngine(CONFIG_PATH) 
    \#在函数内部使用app.config['engine']可获取从外部传入的参数,此处是KGQAEngine(CONFIG_PATH) 
    存在函数:
    def _query(q, verbose=False): 
	    res = app.config['engine'].answer(q)
    

 2. 

 


