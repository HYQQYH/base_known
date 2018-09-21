### 项目相关

 1. flask中,从外部传参给函数内部:
>`from flask import app`<br>
`app.config['engine'] = KGQAEngine(CONFIG_PATH)` <br>
    \#在函数内部使用app.config['engine']可获取从外部传入的参数,此处是KGQAEngine(CONFIG_PATH) <br>
    存在函数:<br>
`def _query(q, verbose=False):` <br>
&emsp;&emsp;`res = app.config['engine'].answer(q)`
    
 2.  网页端flask打开方式:
 >1.先启动flask_http_service/flask_app.py 5000<br>
   2.再启动flask_web_client/flask_app.py 5001<br>
注:1.中的flask调用engine中的client.py查询数据库 2.中的flask调用1中的结果.

 3. 另一种测试方式,启动flask_app.py后,使用curl命令在另一新开终端中发送命令.
 >`curl -i -H "Content-Type:application/json" -X POST -d '{"query":"hinton发表的文章"}' http://10.10.111.250:5000/graph/query`<br>
 如果启动的是本地的服务器,后面的地址应改为相对应的地址,如:<br>
curl -i -H "Content-Type:application/json" -X POST -d '{"query":"hinton发表的文章"}' http://0.0.0.0:5000/graph/query

 4. 单元测试运行方式:`python3 -m pytest -s tests/test_engine.py` #-s参数可以在终端中看到test输出

 5. 日志logging模块：http://www.cnblogs.com/dkblog/archive/2011/08/26/2155018.html
 6.  sys.argv[]是用来获取命令行参数的，sys.argv[0]表示代码本身文件路径，所以参数从1开始。
 7.  npm install 速度慢 
>换为国内镜像：<br>
`npm install --registry=http://registry.npm.taobao.org`<br>
永久设置：<br>
`npm config set registry http://registry.npm.taobao.org `

 8. python3.6下虚拟环境中安装pyfst:
 >`pip3 install pyyaml`<br>
 >`python setup.py install` #第三方安装 ,进入thirdparty/pyfst目录

 11. pickle load: no module named xxx
 > 在将类保存为二进制pickle文件，再次进行load时，需要能够找到类的模块地址，解决方法可参考：https://stackoverflow.com/questions/2121874/python-pickling-after-changing-a-modules-directory

 12. 使用pipreqs生成项目工程的requirements.txt
 > `pipreqs path/to/project`