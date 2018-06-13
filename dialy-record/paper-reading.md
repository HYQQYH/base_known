# paper-reading

## 期刊：

1. Medical Image Analysis
2. IEEE
3. [wiley online library](https://onlinelibrary.wiley.com/journal/15222594)
4. [Biomedical Signal Processing and Control](https://www.journals.elsevier.com/biomedical-signal-processing-and-control/)

### Recurrent Residual Convolutional Neural Network based on U-Net(R2U-Net) for Medical Image Segmentation

* 应用: 提出`RU-Net`/ `R2U-Net`进行视网膜血管分割、皮肤癌分割及肺组织分割。
* 数据：视网膜图像(DRIVE, STARE, CHASE_DB1)、皮肤癌图像(from Kaggle)、肺图像(from Kaggle)
* High Light:
    1. 提出两个新模型：`RU-Net`/ `R2U-Net`，利用了U-Net, Residual Network, RCNN的优点。
    2. 在3种不同模态的图像上进行分割实验。
    3. 采用`patch-based`的方法，`end-to-end`分割。
* 其他知识点：
    1. `patch-based`方法可以解决类别不平衡问题。
    2. 当样本数量较少时，可以采用`leave-one-out`的方法，每次留出一个样本进行测试，其他样本用于训练。每个样本都被进行测试。

### Recurrent Convolutional Neural Network for Object Recognition

* 应用: 提出了循环卷积神经网络。
* High Light:
    1. 在每个卷积层中使用循环卷积操作，这样做的好处是：当前层可以利用上下文的信息，相当于扩大了感受野(RF)。正常的卷积神经网络要达到同样的效果往往需要增加卷积层数，当前层看到的感受野是固定的。
    2. 加入循环卷积层可增加网络的深度，同时将可训练参数保持在constant级别。RCL层之间的权重共享。
    3. 论文认为，虽然在正常卷积神经网络中通过增加网络的深度也可以达到与RCNN同样的深度，且参数量差不多,但这种网络的性能不如RCNN，作者归因于深层的卷积神经网络难以学习。
    4. 时间展开的RCNN实际上是一个在输入层到输出层之间有多条路径的CNN，路径长的有助于学习到深层次的特征，路径短的有助于反向传播。(这里有点疑问，当时间长度固定后，那么路径长度不也固定了么？这种情况下也就不存在多条路径了吧)

### Detecting Cancer Metastases on Gigapixel Pathology Images

* 应用: 检测超大病理学图片是否含有癌细胞
* High Light:
* 知识点:
    1. 如何处理超大图片(10,000 * 10,000):采用patch-based的方法.
    2. 类别不平衡问题:每个slide可以得到10,000-400,000 patches, 含tumor的slide可以得到20-150,000patches不等.为解决类别不平衡问题,normal和tumor得按比例采样.
    3. data augmentation:解决正例样本少的问题,本文中指tumor patch少.方法包括 旋转,左右反转,色彩变换
    4. 利用heat-map来展示检测病变位置.

### 3D U-Net: Learning Dense Volumetric Segmentation from Sparse Annotation

* 应用: 三维图像的分割
* High Light: 数据稀疏标注, 2D U-Net的变体, 开源, caffe实现
* 知识点: