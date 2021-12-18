
### 小样本图像分类的论文的学术地图记录
[目标榜单-SOTA]https://few-shot.yyliu.net

[PaperWithCode]https://paperswithcode.com/task/few-shot-image-classification

### :sparkling_heart: 提出问题
- 1：CNN观察到local的信息，使用Attention机制观察global的信息
- 2：将Transformer的时间复杂度由（H^2*W^2）降低到（H^2+W^2）使用拼接的方式；Q*k-Q+K
- 3：解决怎么看，看哪里，如何看，看多久（看清楚）的问题-神经科学的知识
- 4；解决为什么vision Transformer在小数据集上不行（参数量过大）
- 5：论文中的SCR和CCA都是逐点卷积，这样的时间和空间复杂度有点大！
- 6：在CCA模块阶段丢失了C做卷积，在过往的cross-attention不应该丢掉C的维度吧？
- 7：self-attention 可以看做可分离卷积（SpeConv）SCR和CCA模块都是用可分离卷积，好像有些问题？
- 8: 为什么注意力机制或者注意力机制和卷积结合的方式对小样本有效果呢?
- 9: channel是640维度,spatial是5*5的,如何从channel和spatial创新呢?
-10: resnet+long-range depency的问题如何解决?
-11: CBAM和SeNET以及其他的是Spatial和Channel相互独立计算,并没有太多的交流,如何解决这个问题呢?
-12: 设计多尺度的跳跃链接链接Attention,设计一个综合的Attention模块
### :rainbow: 核心创新点：
- 0：提出一种端到端的可以学习到显式和隐式的representations
- 1：使用数据增强的方式避免数据过拟合（训练的方式）使用Transductive还是inductive的方法？
- 2：将Transformer应用在小数据集上，突破了小数据集的瓶颈；在self-attention继续Transformer解决看的更清楚
- 3：提出针对小样本图像分类的的Transformer或者based Transformer或者结合CNN结合的网络框架
- 4：提出通用的针对小样本图像分类的结合Spatial、Channel、Branch和Temporal的Attention结构
- 4：将图片使用多尺度的网络84=7*3*4 patch划分成21、12、28的三种方式作为patch，参考patch is all you need！
- 5：where/how/which/when to attend -》channel/spatial/temporal/branach attention 
- 6：SCR模块换成Transformer(Self-Attention)，SCR的本质是Self-Attention CCA的本质是Cross-Attention
- 7：将图片分成两种，一种是用CNN和Attention机制，另一种是使用CeiT，两者作为embedding结合提取不同尺度的特征
- 8: 模型压缩:CBAM和SCR以及SENEt都需要大量的参数,这里提出一种pamaters-free的方式
- 9: +和*的操作如果给对应的添加相应的权重-公式的创新
-

### :star2: 待做的消融实验
- 1：postional的问题：先做self-attention（local representation）还是先做cross-attention（global representation）
- 2：证明不单是增加模型的复杂度使用更深的网络更多的卷积达到的效果
- 3：有必要在SCR模块将模型变成四维的部分？4D卷积有什么用，探究去掉4D卷积的效果；小数据集在高维空间的表示如何？
- 4：什么时间模型需要权重共享，在哪里需要权重共享，为什么需要权重共享？
- 5：将Transformer应用在小数据集上，可以针对老的Transformer进行对比实验，与经典的模型进行对比实验
- 6: 和SeNEt/Nonlocal/tripleNet/CBAM/BAM对比Attention模块
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


### :fire: 日常工作记录
- [x] 完成ATTENTIONAL CONSTELLATION NETS 的论文阅读+[调通代码](https://github.com/TJUdyk/ConstellationNet)
- [x] 完成ReNEt的代码详细阅读 -打印出来Cross的图片
- [ ] 找到CrossAttentionNetwork的代码阅读和使用   
- [ ] 读代码：Constellation的代码阅读-Spatial attention和channelAttention
- [x] 读CBAM和BAM看Spatial、attention、channel、和Branach的Attention如何结合
- [x] 统一Spatial、Channel、Tempory、Branch的Attention机制，提出通用的注意力机制框架
- [ ] 实验的结果的可视化的操作和Cross-attention的代码（微信）
- [x] 读SSformer的论文(已完成)看support和quey如何做patch的cross-attention
- [x] 读No-Local的论文看Temporal的attention如何做的
- [x] 读SeNet的论文和代码看channel attention如何做的，获得global context feature
- [ ] 读ConvMix的代码和论文（已完成），使用channel attention
- [ ] 参考论文vision permutator和S2MLPv2找到Branach attention相关的

### :banana: 注意力机制的论文 
- 最新的计算机视觉注意力机制(Attention)综述！[知乎Link](https://zhuanlan.zhihu.com/p/438524916)
- Patches are all you need?[知乎Link](https://www.zhihu.com/question/492712118/answer/2173720753)[PaperWithCode](https://paperswithcode.com/paper/patches-are-all-you-need)
- NeurIPS2021 港大&腾讯AI Lab&牛津提出：CARE，让CNN和Transformer能在对比学习中“互帮互助”！[CSDN Link](https://blog.csdn.net/moxibingdao/article/details/121219821)
- [ ] Are we ready for a new paradigm shift? A Survey on Visual Deep MLP [还在纠结CNN还是Transformer？清华发表一篇survey：全连接层才是终极答案！](https://zhuanlan.zhihu.com/p/437157898)
- [ ] 清华提出：最新的计算机视觉注意力机制综述(Attention)https://zhuanlan.zhihu.com/p/438524916
- [ ] 注意力机制（Visual Attention）https://zhuanlan.zhihu.com/p/324245989
- [ ] 注意力机制的Spatial Domain和Channel Domain https://blog.csdn.net/weixin_39552472/article/details/110746151

### :apple: 对自己提出一些问题
- Global Avg Pooling的作用GAP+FC的组合
- branach Attention 分别沿着HWC的三个channel做branch attention  参考论文vision permutator和S2MLPv2
- 1*1卷积：好处是可以允许不同的channel和Spatial locations交流；坏处：让patch不再互相联系和receptive field消失
- 3*3卷积：receptive field受限制于neighbourhood来获得local representation，更大的receptive field对visual understanding很重要
- self-attention 可以看做可分离卷积（SpeConv）SCR和CCA模块都是用可分离卷积
- SCR模块使用1*1的卷积，但CCA模块不能使用
- vision Transformer make the pardigam shift to the area of global receptive field
- CNN的优点：inductive biases1：translation invariance和local connectivity
- 使用更大的卷积核来替代MLP和self-attention（可以mix distant Spatial locations）
- CBAM和SeNEt 需要获得number of learnable paramaters的参数

### :sparkling_heart: 待实现的github仓库
- [sicara/easy-few-shot-learning](https://github.com/sicara/easy-few-shot-learning)
- [icoz69/DeepEMD](https://github.com/icoz69/DeepEMD)
- [liulu112601/URT](https://github.com/liulu112601/URT)
- [dvornikita/fewshot_ensemble](https://github.com/dvornikita/fewshot_ensemble)
- [peymanbateni/simple-cnaps](https://github.com/peymanbateni/simple-cnaps)
- [Li-ZK/DCFSL-2021](https://github.com/Li-ZK/DCFSL-2021)
- [xhw205/Domain-specific-Fewshot-Learning](https://github.com/xhw205/Domain-specific-Fewshot-Learning)
- [plai-group/simple-cnaps](https://github.com/plai-group/simple-cnaps)
- [ArmanAfrasiyabi/associative-alignment-fs](https://github.com/ArmanAfrasiyabi/associative-alignment-fs)
- [Shandilya21/Few-Shot](https://github.com/Shandilya21/Few-Shot)
- [XiSHEN0220/SSR](https://github.com/XiSHEN0220/SSR)
- [wbw520/MTUNet](https://github.com/wbw520/MTUNet)
- [arjish/PreTrainedFullLibrary_FewShot](https://github.com/arjish/PreTrainedFullLibrary_FewShot)
- [giovcandido/prototypical-networks](https://github.com/giovcandido/prototypical-networks)
- [chrisyxue/RCN_for_Interpretable_few_shot](https://github.com/chrisyxue/RCN_for_Interpretable_few_shot)
- [zoraup/SPNet](https://github.com/zoraup/SPNet)
- [GuChenghs/MCRNet](https://github.com/GuChenghs/MCRNet)
- [PRIS-CV/BSNet](https://github.com/PRIS-CV/BSNet)
- [ctom2/latent-space-transform](https://github.com/ctom2/latent-space-transform)
- [s-a-malik/multi-few ](https://github.com/s-a-malik/multi-few)
- [chrisyxue/RMN-RPN-for-FSL]( https://github.com/chrisyxue/RMN-RPN-for-FSL)
- [Kostis-S-Z/exploring_meta](https://github.com/Kostis-S-Z/exploring_meta)
- [zixuan-chen/few-shot-image-classification](https://github.com/zixuan-chen/few-shot-image-classification)
- [KamalM8/Few-Shot-learning-Fashion](https://github.com/KamalM8/Few-Shot-learning-Fashion)
- [Rajeshyd0308/Few_Shot_Image_Classification ](https://github.com/Rajeshyd0308/Few_Shot_Image_Classification)
- [JoeyLr/Few-Shot-Classification-with-Siamese-Network](https://github.com/JoeyLr/Few-Shot-Classification-with-Siamese-Network)
- [ArmanAfrasiyabi/MixtFSL-fs ](https://github.com/ArmanAfrasiyabi/MixtFSL-fs)
- [cv21rgt/Eye-Disease-Classification-Few-Shot-Learning](https://github.com/cv21rgt/Eye-Disease-Classification-Few-Shot-Learning)

