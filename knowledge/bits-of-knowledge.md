**base knowledge**
-------------
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
