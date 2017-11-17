**base knowledge**
-------------
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




 


