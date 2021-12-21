相关工作
注意力机制告诉我们看哪里,怎么看,看什么,什么时间看的,目标是使用Attention机制扩大表示区域.
CBAM:Convolutional Block Attention Module:这篇文章提出了通道和空间注意力区域的注意力模块,可以嵌入任何CNN结构中,端到端的可训练模型.
放图,放公式介绍
通道注意力机制:使用全局平均池化和最大池化来利用不同的信息;输入一个H*W*C的特征F,分别进行一个空间的全局平均池化和最大池化得到两个1*1*C的通道描述.然后分别送入一个两层的神经网络,第一层神经元个数为C/r,激活函数为Relu;第二层神经元个数为C.两个特征相加经过Sigmod会激活函数权重得到权重系数M,最后拿权重系数和原来的特征F相乘得到缩放后的新特征;
空间注意力机制:输入一个H*W*C的特征F,分别进行一个通道唯独的平均池化和最大池化得到两个H*W*1的通道描述,并将两个描述按通道拼接在一起.然后经过一个7*7的卷积层,激活函数为sigmod得到权重系数M,最后拿权重系数和原来的特征F相乘得到缩放后的新特征;
消融实验部分:引入通道注意力模块同时引入最大池化和平均池化可以得到最好的效果;
消融实验部分2:空间注意力模块中,同时引入最大池化和平均池化比使用一个1*1的卷积要好,卷积层使用7*7的卷积核比3*3的卷积核好;
BAM:Bottleneck Attention Module:
文章的重点放在Attention对神经网络的影响上,提出一种简单有效的Attention模块,通过通道和空间注意力机制,得到一个注意力图区域.
针对通道注意力机制:
针对空间注意力机制:
Squeeze and Excitation Networks:

Stand-Alone Self-Attention in Vision Models:
卷积操作在视觉任务中存在locality限制,CV为了捕捉长距离依赖引入Attention机制,之前引入Attention Block是卷积增强的操作.这篇文章建立了一个完全Attention的网络来验证self-attention可以单独作为一个layer;
Cross-Attention Network for few-shot classification:

Relation Embedding for Few-shot Classification:

Few-shot Classification via Adaptive Attention:我们提出一个创新的小样本学习的方法可以快速优化和适应基于小样本的查询样本表示;我们设计出一种简单的有效的meta-reweighting策略
Attention Mechanisms in Computer Vision A survery
文章里面提出了两个模块self-correlational Representation(SCR)模块和Cross-Correlation Attention(CCA)模块
解决了两个问题what to observe 和where to observe
