**base knowledge**
-------------
### Vim $ linux知识

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

 6. 关于awk的一个应用:
 >NR,表示awk开始执行程序后所读取的数据行数.
FNR,与NR功用类似,不同的是awk每打开一个新文件,FNR便从0重新累计.
 >现在有两个文件格式如下：
\#cat account
张三|000001
李四|000002
\#cat cdr
000001|10
000001|20
000002|30
000002|15
想要得到的结果是将用户名，帐号和金额在同一行打印出来,如下:
张三|000001|10
张三|000001|20
李四|000002|30
李四|000002|15
执行如下代码
    \#awk -F \| 'NR==FNR{a[\$2]=\$0;next}{print a[\$1]"|"\$2}' account cdr
注释:
由NR=FNR为真时,判断当前读入的是第一个文件account,然后使用{a[\$2]=\$0;next}循环将account文件的每行记录都存入数组a,并使用\$2第2个字段作为下标引用.
由NR=FNR为假时,判断当前读入了第二个文件cdr,然后跳过{a[\$2]=\$0;next},对第二个文件cdr的每一行都无条件执行{print a[\$1]"\|"\$2},此时变量\$1为第二个文件的第一个字段,与读入第一个文件时,采用第一个文件第二个字段\$2为数组下标相同.因此可以在此使用a[$1]引用数组。

 7. 从文件中随机抽取内容:
 >`while read line; do echo "$line:$RANDOM"; done < temp | sort -k2,2 -t ':' -n | awk -F ':' 'NR<=5{print $1}'`
 >解释:\$line为当前行内容,\$RANDOM为在行内容后添加一个随机数,用':'进行分隔,sort -k2,2 -t ':' -n只对用':'进行分隔的第二个域进行排序,-n为升序排序,最后的awk输出前5行内容,分隔符为':'.
 >关于sort排序的参考链接:http://man.linuxde.net/sort

 8. 去除重复行
   > :g/^\(.*\)\$\n\1$/d                      //去除重复行
 shell脚本中去重:`sort -u input-file -o output-file`
 

 9. 使用awk命令对文件内容进行洗牌:

 >awk 'BEGIN{srand()}{b[rand()NR]=$0}END{for(x in b)print b[x]}' test_result1 >> test

 10. 使用sed命令行去掉 <200b>
  `sed -i 's/\xe2\x80\x8b//g' inputfile`
  
 11. 按第2列对文件内容进行排序,分隔符为tab: 
 >sort -n -k 2 -t \t test.txt -o test.txt
 -o命令表示将排序后的内容存储于原文件中.
 

 12. 提取recodeId:
`grep '"core": "/data/chat"' log/$yesterday.log | grep -o -P '"recordId": ".*?"' | awk -F ':' '{print $2}' | sed 's/"//g' > recordId/$yesterday.recordId`

 13. ls -lt:按时间排序.
 14. gf可打开光标下的路径，ctrl+o可退回之前页面
:tabnew[file]，在tab页中编辑打开文件，gt进行页面切换
shift + #:查找光标所在字符串

 15. 去掉vim 中的^M符号
 >：%s/^M//g
tr -d "\015" <douban_que_ans2> douban_que_ans3

 16. `grep -n http://tieba.baidu.com/f?kw=%E5%91%A8%E6%9D%B0%E4%BC%A6 spider-tieba_2017-05-05-09:02:39.log | grep -o '\[http.*\]' | sort -u`
 17.  `grep -P -o '<a href.*?class="j_th_tit ".*?</a>' tieba.html` 结果如下：
`<a href="/p/5089096303" title="`【JayCn】【地表最强】" target="_blank" class="j_th_tit ">【JayCn】【地表最强】`</a>`

 18. 终端命令：`Shift+Ctrl+T` 打开新的标签页
`ctrl + pageUp ctrl + pageDown`可在多个屏幕中进行切换

 19. `python tiebacontentParser.py | tee tieba.htm`,查看爬取的htm页面，tee指令会从标准输入设备读取数据，将其内容输出到标准输出设备，同时保存成文件。
 20.  yw //复制从光标开始到词尾的字符。ndw或ndW：删除光标处开始及其后的n-1个字
 32. grep 'failed to parse' log/spider-shiwanwhy_2017-04-24-11:14:22.log | awk -F 'with parser' '{print $2}' | sort -u
 33. du -sh pages:查看文件大小。
wc -l pages：查看文件数量
 42. `sed 's/=>/%/g' examples/data/AI_industry/rules/mannully_rules.txt | sort -k 2 -t "%" | sed 's/%/=>/g' | less`该命令实现将文件中的`=>`替换为`%`号,然后以`%`为分隔符,以第二列内容进行排序,排序后在将`%`替换回`=>`.
 43. 保留复制的格式：`:set paste`
 44. 关于BASH_SOURCE
 > `DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd )"`得到shell脚本文件所在完整路径（绝对路径）及文件名（无论source,sh,.三种调用方式），且不改变shell的当前目录。
 > 参考链接:http://blog.csdn.net/zhaozhencn/article/details/21103367