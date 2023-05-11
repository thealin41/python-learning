# 基本原理
持续学习(Continual Learning)算法试图为神经网络实现像人们一样学习大量不同的任务，不出现任何负面的相互干扰， 并解决灾难性的遗忘问题。持续学习算法的重点不是如何利用在以前任务中学到的知识来帮助更好地学习新任务，而是解决灾难性遗忘的问题。

参考文献：
* [最新综述 | 类别增量学习研究进展和性能评价](https://www.zhuanzhi.ai/vip/cf8a64587dc628dab1cca6945b98a751) 全文链接[类别增量学习研究进展和性能评价](https://github.com/bettermorn/IAICourse/blob/main/refermaterials/papers/%E7%B1%BB%E5%88%AB%E5%A2%9E%E9%87%8F%E5%AD%A6%E4%B9%A0%E7%A0%94%E7%A9%B6%E8%BF%9B%E5%B1%95%E5%92%8C%E6%80%A7%E8%83%BD%E8%AF%84%E4%BB%B7.pdf)
* [让模型实现“终生学习”，佐治亚理工学院提出Data-Free的增量学习](https://mp.weixin.qq.com/s/Fm9ufPD6rzL2VzaqpdFpjg)
* [万文长字总结「类别增量学习」的前世今生、开源工具包](https://mp.weixin.qq.com/s/A472p7XGZMhAMAR2wyHZJw)
* 论文和代码汇总：
https://paperswithcode.com/task/incremental-learning

# 1.Incremental Classifier and Representation Learning
## 原理
Incremental Classifier and Representation Learning
针对图像分类网络的增量学习，让网络在保留旧类别区分能力的基础上，区分新类别，提出了一种名为iCaRL的训练策略，该算法可以让分类器（例如softmax分类器）与特征提取器（例如CNN）同时学习。

![image](https://user-images.githubusercontent.com/568965/232740779-58158fb8-ddf3-4e9d-938b-2785c3ec9873.png)
## 增量训练的流程
* 添加新类别数据后，训练CNN与全连接层分类器
* 减少旧类别的examplar的容量，去除部分训练数据
* 构造新类别的examplar，存储部分新类别的训练数据

## 准确率提升的原因
* 使用新数据与部分旧数据微调网络
* 使用更为鲁棒的分类算法——最近邻kNN

## 论文和代码
iCaRL: Incremental Classifier and Representation Learning
* https://arxiv.org/pdf/1611.07725v2.pdf

* https://paperswithcode.com/paper/icarl-incremental-classifier-and#code
##  开源框架 PyCIL[13]
Methods Reproduced
* FineTune: Baseline method which simply updates parameters on new task, suffering from Catastrophic Forgetting. By default, weights corresponding to the outputs of previous classes are not updated.

* EWC: Overcoming catastrophic forgetting in neural networks. PNAS2017 [paper]

* LwF: Learning without Forgetting. ECCV2016 [paper]

* Replay: Baseline method with exemplars.

* GEM: Gradient Episodic Memory for Continual Learning. NIPS2017 [paper]

* iCaRL: Incremental Classifier and Representation Learning. CVPR2017 [paper]

* BiC: Large Scale Incremental Learning. CVPR2019 [paper]

* WA: Maintaining Discrimination and Fairness in Class Incremental Learning. CVPR2020 [paper]

* PODNet: PODNet: Pooled Outputs Distillation for Small-Tasks Incremental Learning. ECCV2020 [paper]

* DER: DER: Dynamically Expandable Representation for Class Incremental Learning. CVPR2021 [paper]

* Coil: Co-Transport for Class-Incremental Learning. ACM MM2021 [paper]
 
##  开源框架 avalanche
https://avalanche.continualai.org/getting-started/learn-avalanche-in-5-minutes
https://github.com/ContinualAI/avalanche
# 增量学习需要注意的问题
## 1. 如何避免过拟合？
* 正则化：L1和L2
* 早停止：
* 数据增强： 旋转、平移、缩放
* Dropout：随机删除神经元
* 稀疏表示：减少特征之间的冗余信息
* 集成学习：多个模型加权平均，提高泛化能力
## 2. 如何处理新数据和旧数据之间的差异
* 更新参数适应新的数据分布
* 增量学习算法：IPCA、ILDA
* 数据增强技术：旋转、平移、缩放
* 迁移学习技术：知识蒸馏、迁移学习
