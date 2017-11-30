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

 4. List item