###关于python

 1. argparse是python用于解析命令行参数和选项的标准模块，用于代替已经过时的optparse模块。
 >使用步骤如下:
 >1：import argparse
 >2：parser = argparse.ArgumentParser(description='...') #一般只需传进description参数
 >3：parser.add_argument() 
 >\#常见参数如:命令行参数名或选项,dest,action,metavar,required,help,type,default
 >4：parser.parse_args()
 >
 >例子如:
 >`parser.add_argument('-w','--weight',dest='weight',action='store',metavar='number',required=False,default=-1,type=float,help='weight number')`
 >令args = parser.parse_args()
 >1.dest参数的存在,允许如下访问方式:args.weight,若上述例子中不存在dest,但存在`'--weight'`,也可使用args.weight访问参数.
 >2.上述例子允许在命令中以`-w 3.4`或`--weight 3.4`的方式传进参数.
 >3.required参数为False,表明该参数非必须.
 >4.type参数,指明该参数的类型.default为其默认的值
 >5.store 保存参数值，可能会先将参数值转换成另一个数据类型。若没有显式指定动作，则默认为该动作。
 >参考链接:https://www.cnblogs.com/lovemyspring/p/3214598.html

 2. 使用configparser读取配置文件:
 >1.cf = configparser.ConfigParser(
            interpolation=configparser.ExtendedInterpolation())
 >2.cf.read(CONFIG_PATH)
 >3.local_log_path = cf.get("logging", "local_log_path")
 >配置文件形如:
 >[logging]
 >local_log_path = local.log
 >解释:[]包含的叫section,    section 下有option=value这样的键值
 >使用handler interpolation=configparser.ExtendedInterpolation()允许配置文件中使用类似参数的方式,如:
 >[Common]
 >system_dir: /System
 >[Frameworks]
 >Python: 3.2
 >path: \${Common:system_dir}/Library/Frameworks/
 >ExtendedInterpolation使用${section:option}来表示来自外部section的值.
 >

 3. 获取文件夹下的所有文件名:
 `lists = os.listdir(db_path)` #db_path为一个文件夹目录
 `for classname in lists:`
  ....   `filepath = os.path.join(db_path,classname)` #可得到文件夹下每个文件的所在路径
  `os.path.isdir(filepath)`#判断是否为文件夹
  `os.path.isfile(filepath)`#判断是否为文件

 4. 在python脚本中使用os.system(dot -Tpdf -o test.dot),相当于在终端命令中执行dot -Tpdf -o test.dot,以上命令生成一个pdf文件,输入为.dot文件
 5. 使用@property装饰器把一个方法变成属性进行调用,@property广泛应用在类的定义中，可以让调用者写出简短的代码，同时保证对参数进行必要的检查，这样，程序运行时就减少了出错的可能性。参考链接:https://www.liaoxuefeng.com/wiki/001374738125095c955c1e6d8bb493182103fac9270762a000/001386820062641f3bcc60a4b164f8d91df476445697b9e000
 6. \__str__特殊方法,类似与\__init__方法,主要用于定义类中,按特定格式打印出类的实例.供print调用,方便调试.http://blog.csdn.net/luckytanggu/article/details/53649156
 > 注意:若类中实现了\__str__函数,则`str(A)`(A为类对象),效果等同于`print(A)`
 

 7. 新建虚拟环境:
 > `python3.6 -m venv env`
 

 8. @classmethod与@staticmethod:
 >classmethod 修饰符对应的函数不需要实例化，不需要 self 参数，但第一个参数需要是表示自身类的 cls 参数，可以来调用类的属性，类的方法，实例化对象等
 >class A(object):
 >def func(cls):
 >pass
 >print(A.func())
 >staticmethod不能调用类的属性，方法，不需要self参数及cls参数。与类无关，但该类需要该方法时可以将函数定义为staticmethod。