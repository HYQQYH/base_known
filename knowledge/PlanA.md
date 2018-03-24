###知识总结 
 
 1. 为什么fst的结果要优于trie
 > fst为最大片段匹配,前缀后缀无关,trie要求从头匹配.
 > fst解析时间耗时短,当rule很大时,trie读取耗时长.
 
 2. 在nmt中为什么短句的预测结果要优于长句的预测结果?
 > 可通过使用attention mechanism改善长句的预测结果.
 
 3. 神经网络训练中为何会出现梯度消失及梯度爆炸：
 >https://zhuanlan.zhihu.com/p/25631496
 >减少梯度消失或梯度爆炸可用如下方法：
 >1）梯度消失：激活函数使用relu代替sigmoid or tanh
 >2）梯度爆炸：gradient clipping梯度裁剪，如果在一次迭代中各个权重的梯度平方和大于某个阈值，那么为避免权重的变化值太大，求一个缩放因子（阈值除以平方和），将所有的梯度乘以这个因子
 >3）学习长时依赖: 将输入进行反转（翻译应用中的trick，暂不明为何可以缓解梯度消失及梯度爆炸）
 >4) recurrent weights 初始化为 identity matrix(Roger Grosse),但也有说初始化为‘正交矩阵’，为什么能缓解梯度消失及梯度爆炸，原因不明。

 4. 关于RNN、LSTM的反向传播推导可参考文献：
 >A Gentle Tutorial of Recurrent Neural Network with Error Backpropagation

 5. 关于训练的一些技巧：
 >1) learning rate decay: starting with a higher learning rate, then gradually reducing
the learning rate near the end of training.
 >2) early stopping: As another method to prevent over-fitting and smooth convergence of training, it is common to measure log likelihood on a held-out development set, and when the log likelihood stops improving or starts getting worse, reduce the learning rate.
 >3）Shuffling training order

 6. seq2seq中的一些trick:
 >  长序列：attention, bigger state
 >  欠拟合：bigger hiddern state, deep lstm + skip connections
 >  过拟合：dropout + ensembles

 7. 关于attention
 >1) attention包括global attention和local attention, 计算at时，global attention需要source的每一个时刻的信息，不利于长序列的应用。local attention只关注source的子序列。

 8. 需要弄清楚在nmt中各个参数的含义及其用法，如何调参的。
 9. sample softmax: 当目标词表很大时，可以通过sample softmax降低训练时的解码复杂度，可参考博客：http://blog.csdn.net/MebiuW/article/details/68952814
 10. beam search
 12. CNN中的一些优化方法：
 > 1) 参数初始化(打破对称性，降低梯度消失现象)：(0, 0.01)的高斯分布、xavier 、orthonormal matrix initialization
 > 2) 随机梯度下降SGD
 > 3) batch normalization: reduces internal covariant shift、enables the use of higher learning rate、reduces the need for Dropout
 > 4) Shortcut connections

 13. 激活函数的优缺点
 > 1) sigmoid:  
 > a. Saturated neurons “kill” the gradients. 
 > b. Sigmoid outputs are not zerocentered
 > c. exp() is a bit compute expensive
 > 2) tanh:
 > a. zero centered
 > b. still kills gradients when saturated
 > 3) ReLU
 > a.does not saturate
 > b. very computionally efficient
 > c. converges much faster than sigmoid/tanh in practice
 > d. not zero-centered output

###支持向量机

 1. 支持向量机处理非线性可分的情况：
 > 1) 需要使用一个非线性映射将原始数据变换到高维空间（高维空间中线性可分，VC维原理）。
 > 2) 在特征空间中使用线性分类器学习分类。

 2. 核函数
 > 核函数的价值在于它虽然也是将特征从低维空间映射到高维， 但核函数仅通过低维计算就可把分类效果映射到高维上， 避免了高维空间中的组合爆炸问题。

 3. 含噪声的支持向量机分类（离群点的松弛变量）
 > 引入松弛变量，允许数据点一定程度上偏离超平面。
 > 优化目标增加惩罚项。
 > 引入惩罚因子的好处：解决数据unbalanced问题，如可对样本数量少的负类更大的惩罚因子，表示我们重视这部分样本。

###分类结果评估

 1. 精确率|召回率:https://www.zhihu.com/question/19645541

###常用机器学习算法

 1. 用于分类：KNN、朴素贝叶斯、SVM、决策树
 2. 用于聚类：K-means
 3. 维度约简：PCA
 4. 数据预处理：标准化、去除均值率和方差缩放、正规化、二值化
 5. 模型选择：交叉验证、网格搜索、验证曲线

###机器学习、深度学习知识点总结及面试题：

https://mp.weixin.qq.com/s?__biz=MzA4NzE1NzYyMw==&mid=2247496101&idx=2&sn=3e61ce52d45906d01ef82bdb1dd6ebe9&chksm=903f0fbda74886ab6e7306d5cc9882e0c1a67acc704c190c76557859f2e80e1c5585c22de932&mpshare=1&scene=1&srcid=0318vwyKYZYAVUlfG7wXAgPS&pass_ticket=olmUPhHgWYcVWy1%2FLxx5uyOEWCDB5qKQjgZXZy88JfIIt8FvmDL7D9Ju2K5RTzqp#rd
###深度学习中的五大正则化方法和七大优化策略：
  https://mp.weixin.qq.com/s?__biz=MzA4NzE1NzYyMw==&mid=2247495766&idx=3&sn=09c34414d559d4843705b7d08a8c20a2&chksm=903f0e4ea748875814e4b6caa7fafea1a03a8598ebc81476fb30a41306b8cc3a50bd39d7a598&scene=0&pass_ticket=olmUPhHgWYcVWy1%2FLxx5uyOEWCDB5qKQjgZXZy88JfIIt8FvmDL7D9Ju2K5RTzqp#rd

###深度学习的这些坑你都遇到过吗？神经网络 11 大常见陷阱及应对方法 :
https://mp.weixin.qq.com/s?__biz=MzI3MTA0MTk1MA==&mid=2652004081&idx=4&sn=d28fc6c3ac2f631aab08611877fdde6f&chksm=f1212a00c656a316d0aeba042af5406cef0177132f5001d5d4a6cc05cd804e634c178602270f&mpshare=1&scene=1&srcid=0907mQ9O6t2mq95xN0502JWo&pass_ticket=olmUPhHgWYcVWy1%2FLxx5uyOEWCDB5qKQjgZXZy88JfIIt8FvmDL7D9Ju2K5RTzqp#rd

###TensorFlow的55个经典案例
https://mp.weixin.qq.com/s?__biz=MzA4NzE1NzYyMw==&mid=2247491928&idx=3&sn=8aa6b60c87e0c912d41f0b78e5a8c090&chksm=903f1f40a7489656e3e70b1fb3b2598761b10bac8517bed303ef48f0dff9e675dabfa34e9bfc&mpshare=1&scene=1&srcid=0318NPqmxS6x5Cf6a8RYxJCm&pass_ticket=olmUPhHgWYcVWy1%2FLxx5uyOEWCDB5qKQjgZXZy88JfIIt8FvmDL7D9Ju2K5RTzqp#rd


###深度学习必备：随机梯度下降（SGD）优化算法及可视化
https://mp.weixin.qq.com/s?__biz=MzI3MTA0MTk1MA==&mid=2651996065&idx=4&sn=cad829251a0655c8b3d11a6b448dd143&chksm=f1214b50c656c246b91c47dc738dba5dd375e8d60a0b220cc8829cc7dfcbc8134401d30a07de&mpshare=1&scene=1&srcid=0318ctyv0vQGoXx6YTf4SH0f&pass_ticket=olmUPhHgWYcVWy1%2FLxx5uyOEWCDB5qKQjgZXZy88JfIIt8FvmDL7D9Ju2K5RTzqp#rd

###18个技巧实战深度学习，资深研究员的血泪教训 
https://mp.weixin.qq.com/s?__biz=MzI3MTA0MTk1MA==&mid=2651994342&idx=5&sn=dbae830cebb360f78f43191cf5d2c7ab&chksm=f1214c17c656c501d3fa7e45fdc9ccc9ada604051663d79153d16d60496e3d15785aeff12d0e&mpshare=1&scene=1&srcid=0318opZH2c8bPWqIRYAp7usO&pass_ticket=olmUPhHgWYcVWy1%2FLxx5uyOEWCDB5qKQjgZXZy88JfIIt8FvmDL7D9Ju2K5RTzqp#rd

###机器学习工程师必须知道的十个算法 
https://mp.weixin.qq.com/s?__biz=MzI3MTA0MTk1MA==&mid=2651986479&idx=4&sn=108b62cd7e983c2866619209d0a504cb&mpshare=1&scene=1&srcid=0318bwzYCKwirsFMWiiiAhiq&pass_ticket=olmUPhHgWYcVWy1%2FLxx5uyOEWCDB5qKQjgZXZy88JfIIt8FvmDL7D9Ju2K5RTzqp#rd

###避免过拟合：

 1. 增加输入数据、数据增强、早停、dropout 及其变体、L1 正则化、L2 正则化、

###七个深度学习实用技巧
http://imgtec.eetrend.com/blog/11289

###基于深度学习的智能问答
https://yq.aliyun.com/articles/58745		

###关于分词、命名实体识别、词性标注、句法分析：
https://blog.csdn.net/hit_lingo/article/details/42639455