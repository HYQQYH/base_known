###关于python

 2. 使用configparser读取配置文件:
 >1.cf = configparser.ConfigParser(
            interpolation=configparser.ExtendedInterpolation())<br>
 >2.cf.read(CONFIG_PATH)<br>
 >3.local_log_path = cf.get("logging", "local_log_path")<br>
 >配置文件形如:<br>
 >[logging]<br>
 >local_log_path = local.log<br>
 >解释:[]包含的叫section,    section 下有option=value这样的键值<br>
 >使用handler interpolation=configparser.ExtendedInterpolation()允许配置文件中使用类似参数的方式,如:<br>
 >[Common]<br>
 >system_dir: /System<br>
 >[Frameworks]<br>
 >Python: 3.2<br>
 >path: \${Common:system_dir}/Library/Frameworks/<br>
 >ExtendedInterpolation使用${section:option}来表示来自外部section的值.

 3. 在python脚本中使用os.system(dot -Tpdf -o test.dot),相当于在终端命令中执行dot -Tpdf -o test.dot,以上命令生成一个pdf文件,输入为.dot文件
 4. 使用@property装饰器把一个方法变成属性进行调用,@property广泛应用在类的定义中，可以让调用者写出简短的代码，同时保证对参数进行必要的检查，这样，程序运行时就减少了出错的可能性。参考链接:https://www.liaoxuefeng.com/wiki/001374738125095c955c1e6d8bb493182103fac9270762a000/001386820062641f3bcc60a4b164f8d91df476445697b9e000
 5. \__str__特殊方法,类似与\__init__方法,主要用于定义类中,按特定格式打印出类的实例.供print调用,方便调试.http://blog.csdn.net/luckytanggu/article/details/53649156<br>
    > 注意:若类中实现了\__str__函数,则`str(A)`(A为类对象),效果等同于`print(A)`

 6. @classmethod与@staticmethod:
 >classmethod 修饰符对应的函数不需要实例化，不需要 self 参数，但第一个参数需要是表示自身类的 cls 参数，可以来调用类的属性，类的方法，实例化对象等<br>
 > class A(object):<br>
 >&ensp;&ensp;def func(cls):<br>
 >&ensp;&ensp;&ensp;&ensp;pass<br>
 >print(A.func())<br>
 >staticmethod不能调用类的属性，方法，不需要self参数及cls参数。与类无关，但该类需要该方法时可以将函数定义为staticmethod。

 7. csv文件在windows中打开乱码的解决方法: 保存csv文件时使用codecs.open(filename,'w',encoding='gbk').

 8. 关于'ascii' codec can't decode byte 0xe7 in position 0: ordinal not in range(128)的问题的解决方法:
 > Python中字符串类型分为byte string 和 unicode string两种。 如果在python文件中指定编码方式为utf-8(#coding=utf-8)，那么所有带中文的字符串都会被认为是utf-8编码的byte string（例如：mystr=”你好”），但是在函数中所产生的字符串则被认为是unicode string。unicode string 和 byte string 是不可以混合使用的.将字符串全都转成unicode string。如'你好'改为u'你好'
 https://blog.csdn.net/u011350541/article/details/78683682

 11. 使用"nohup"， 即 “nohup ./myjob &”，忽略hangup信号，防止shell关闭时程序停掉。(程序后台运行)