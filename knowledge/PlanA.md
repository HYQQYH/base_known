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
 11. CNN中避免过拟合的一些方法:
 > dropout
 > dropconnect
 

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