Deep Learning on Graphs with Keras
====

项目基于 [Semi-Supervised Classification with Graph Convolutional Networks](http://arxiv.org/abs/1609.02907) (ICLR 2017)


版本要求
-----
  * keras (1.0.9 or higher)
  * TensorFlow or Theano
训练入口
-----
```python train.py```


### 卷积定理：
两个函数的卷积等于这两个函数傅立叶变换后的乘积再逆变换回来，也就是说卷积的操作等于傅立叶变换后的乘积操作
###核心思想：
卷积核是个对角阵，为了方便计算，把邻接矩阵的特征值矩阵（也是对角阵）的切比雪夫多项式作为新的卷积核，这样可以把基【基为邻接矩阵的特征向量（两两正交）】
移入切比雪夫多项式函数，这样，只要计算邻接矩阵的切比雪夫多项式就可以了，再将这些多项式的项分别和特征矩阵相乘，拼接以后乘权重，再过激活函数得出结果。
### 对于图卷积的理解：
1. 先求出邻接矩阵A，以及度矩阵D；
2. 求出拉普拉斯矩阵L=D-A；
3. 求出对称归一化拉普拉斯矩阵；
3. 计算对称归一化拉普拉斯矩阵的k阶切比雪夫矩阵多项式【切比雪夫多项式的每一项都是一个卷积核，k的大小为感受视野】；
4. 将特征矩阵与每项切比雪夫项矩阵相乘【这一步就是把卷积核乘以特征矩阵，其实就是对特征矩阵的卷积】，再将结果拼接在一起
5. 乘以权重，得出结果。


[参考] Thomas Kipf, [Graph Convolutional Networks](http://tkipf.github.io/graph-convolutional-networks/) (2016)

