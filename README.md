### Hi there 👋

### :heavy_check_mark: 提出问题
- 1：CNN观察到local的信息，使用Attention机制观察global的信息
- 2：将Transformer的时间复杂度由（H^2*W^2）降低到（H^2+W^2）使用拼接的方式；Q*k-Q+K
- 3：解决怎么看，看哪里，如何看，看多久（看清楚）的问题-神经科学的知识
- 4；解决为什么vision Transformer在小数据集上不行（参数量过大）
- 5：论文中的SCR和CCA都是逐点卷积，这样的时间和空间复杂度有点大！
- 6：在CCA模块阶段丢失了C做卷积，在过往的cross-attention不应该丢掉C的维度吧？
- 7：self-attention 可以看做可分离卷积（SpeConv）SCR和CCA模块都是用可分离卷积，好像有些问题？
### :heavy_check_mark: 核心创新点：
- 0：提出一种端到端的可以学习到显式和隐式的representations
- 1：使用数据增强的方式避免数据过拟合（训练的方式）使用Transductive还是inductive的方法？
- 2：将Transformer应用在小数据集上，突破了小数据集的瓶颈；在self-attention继续Transformer解决看的更清楚
- 3：提出针对小样本图像分类的的Transformer或者based Transformer或者结合CNN结合的网络框架
- 4：提出通用的针对小样本图像分类的结合Spatial、Channel、Branch和Temporal的Attention结构
- 4：将图片使用多尺度的网络84=7*3*4 patch划分成21、12、28的三种方式作为patch，参考patch is all you need！
- 5：where/how/which/when to attend -》channel/spatial/temporal/branach attention 
- 6：SCR模块换成Transformer(Self-Attention)，SCR的本质是Self-Attention CCA的本质是Cross-Attention
- 7：将图片分成两种，一种是用CNN和Attention机制，另一种是使用CeiT，两者作为embedding结合提取不同尺度的特征

### :heavy_check_mark: 待做的消融实验
- 1：postional的问题：先做self-attention（local representation）还是先做cross-attention（global representation）
- 2：证明不单是增加模型的复杂度使用更深的网络更多的卷积达到的效果
- 3：有必要在SCR模块将模型变成四维的部分？4D卷积有什么用，探究去掉4D卷积的效果；小数据集在高维空间的表示如何？
- 4：什么时间模型需要权重共享，在哪里需要权重共享，为什么需要权重共享？
- 5：将Transformer应用在小数据集上，可以针对老的Transformer进行对比实验，与经典的模型进行对比实验，
### :books: 模型结构改进相关的：

- 1：减少模型的参数量，降低模型的参数量，SCR（157.K，CCA45.8K）-**************
- 2：显著性的Co-Saliency的和CO-correlation类似，是否可以尝试改进一下；
- 3：将3*3的卷积使用MHSA替代-（BOTNet的思想）https://www.zhihu.com/question/442344643/answer/1744876036
- 4：为什么在SCR模块卷积部分那里使用5*5的卷积，大卷积和小卷积的区别
- 5：为什么之前SCR模块加入BN和RELU在CCA模块没有加入BN和CCa
- 1：这里提到4D卷积的原因是可以有效逼近原始4D卷积在内存和时间方面的效率？
- 2：为什么SCR模块可以保留丰富的语义信息，但做分类也没有使用语义信息？
- 3：为什么在SCR模块使用relu激活函数呢？

###  :pushpin: 数据集和训练相关的：
- 1：是否还有更好的训练方式，元学习或者其他的，使用Transductive还是inductive的方法？
- 2：在模型的训练过程中，每个数据集在训练集达到84%左右，测试集只有65%，明显模型过拟合！-求均值均到了70%多或者80%多，但明显越训练，越过拟合
- 3：CO-rellation的过程中和元学习有什么关系呢？


