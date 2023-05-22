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

# 方法列表
| 类别          | 方法名称     |    原理重点   |
|:--|:--:|--:|
| 参数正则化|EwC|显式约束重要参数更新, 或者约束梯度更新方向|
| 知识蒸馏|PoDNet，LwF，BiC|保持新旧模型对给定数据 的输出一致性|
| 数据回放|WA，iCaRL|保存一小部分旧类别数据 用于后续再学习|
| 特征回放|IL2A，PASS|保存深度特征空间的旧类 别特征来维持决策面|
| 网络结构|DER，SSRE|冻结已有网络参数, 新参数用于学习新类别|

# 方法比较参考信息
来源全文链接[类别增量学习研究进展和性能评价](https://github.com/bettermorn/IAICourse/blob/main/refermaterials/papers/%E7%B1%BB%E5%88%AB%E5%A2%9E%E9%87%8F%E5%AD%A6%E4%B9%A0%E7%A0%94%E7%A9%B6%E8%BF%9B%E5%B1%95%E5%92%8C%E6%80%A7%E8%83%BD%E8%AF%84%E4%BB%B7.pdf)
3类别增量学习中的知识蒸馏方法
https://github.com/bettermorn/IAICourse/blob/main/img/3%E7%B1%BB%E5%88%AB%E5%A2%9E%E9%87%8F%E5%AD%A6%E4%B9%A0%E4%B8%AD%E7%9A%84%E7%9F%A5%E8%AF%86%E8%92%B8%E9%A6%8F%E6%96%B9%E6%B3%95.png
![3类别增量学习中的知识蒸馏方法]
(https://github.com/bettermorn/IAICourse/blob/main/img/3%E7%B1%BB%E5%88%AB%E5%A2%9E%E9%87%8F%E5%AD%A6%E4%B9%A0%E4%B8%AD%E7%9A%84%E7%9F%A5%E8%AF%86%E8%92%B8%E9%A6%8F%E6%96%B9%E6%B3%95.png)
4 基于数据回放的类别增量学习中的新旧类别偏差校准方法总结
https://github.com/bettermorn/IAICourse/blob/main/img/4%E5%9F%BA%E4%BA%8E%E6%95%B0%E6%8D%AE%E5%9B%9E%E6%94%BE%E7%9A%84%E7%B1%BB%E5%88%AB%E5%A2%9E%E9%87%8F%E5%AD%A6%E4%B9%A0%E4%B8%AD%E7%9A%84%E6%96%B0%E6%97%A7%E7%B1%BB%E5%88%AB%E5%81%8F%E5%B7%AE%E6%A0%A1%E5%87%86%E6%96%B9%E6%B3%95%E6%80%BB%E7%BB%93.png
![4基于数据回放的类别增量学习中的新旧类别偏差校准方法总结](https://github.com/bettermorn/IAICourse/blob/main/img/4%E5%9F%BA%E4%BA%8E%E6%95%B0%E6%8D%AE%E5%9B%9E%E6%94%BE%E7%9A%84%E7%B1%BB%E5%88%AB%E5%A2%9E%E9%87%8F%E5%AD%A6%E4%B9%A0%E4%B8%AD%E7%9A%84%E6%96%B0%E6%97%A7%E7%B1%BB%E5%88%AB%E5%81%8F%E5%B7%AE%E6%A0%A1%E5%87%86%E6%96%B9%E6%B3%95%E6%80%BB%E7%BB%93.png)
6基于样本回放的方法在 CIFAR 100, ImageNet-Sub 和 ImageNet-Full 上的平均增量准确率 (%) 比较
![基于样本回放的方法在 CIFAR 100, ImageNet-Sub 和 ImageNet-Full 上的平均增量准确率 (%) 比较](https://github.com/bettermorn/IAICourse/blob/main/img/6%E5%9F%BA%E4%BA%8E%E6%A0%B7%E6%9C%AC%E5%9B%9E%E6%94%BE%E7%9A%84%E6%96%B9%E6%B3%95%E5%9C%A8%20CIFAR%20100%2C%20ImageNet-Sub%20%E5%92%8C%20ImageNet-Full%20%E4%B8%8A%E7%9A%84%E5%B9%B3%E5%9D%87%E5%A2%9E%E9%87%8F%E5%87%86%E7%A1%AE%E7%8E%87%20(%25)%20%E6%AF%94%E8%BE%83.png)
7基于样本回放的方法在 CIFAR 100, ImageNet-Sub 和 ImageNet-Full 上的遗忘率 (%) 比较
https://github.com/bettermorn/IAICourse/blob/main/img/7%E5%9F%BA%E4%BA%8E%E6%A0%B7%E6%9C%AC%E5%9B%9E%E6%94%BE%E7%9A%84%E6%96%B9%E6%B3%95%E5%9C%A8%20CIFAR%20100%2C%20ImageNet-Sub%20%E5%92%8C%20ImageNet-Full%20%E4%B8%8A%E7%9A%84%E9%81%97%E5%BF%98%E7%8E%87%20(%25)%20%E6%AF%94%E8%BE%83.png
![7基于样本回放的方法在 CIFAR 100, ImageNet-Sub 和 ImageNet-Full 上的遗忘率 (%) 比较](https://github.com/bettermorn/IAICourse/blob/main/img/7%E5%9F%BA%E4%BA%8E%E6%A0%B7%E6%9C%AC%E5%9B%9E%E6%94%BE%E7%9A%84%E6%96%B9%E6%B3%95%E5%9C%A8%20CIFAR%20100%2C%20ImageNet-Sub%20%E5%92%8C%20ImageNet-Full%20%E4%B8%8A%E7%9A%84%E9%81%97%E5%BF%98%E7%8E%87%20(%25)%20%E6%AF%94%E8%BE%83.png)
8 非样本回放类别增量学习方法平均增量准确率 (%) 比较
https://github.com/bettermorn/IAICourse/blob/main/img/8%20%E9%9D%9E%E6%A0%B7%E6%9C%AC%E5%9B%9E%E6%94%BE%E7%B1%BB%E5%88%AB%E5%A2%9E%E9%87%8F%E5%AD%A6%E4%B9%A0%E6%96%B9%E6%B3%95%E5%B9%B3%E5%9D%87%E5%A2%9E%E9%87%8F%E5%87%86%E7%A1%AE%E7%8E%87%20(%25)%20%E6%AF%94%E8%BE%83.png
![8 非样本回放类别增量学习方法平均增量准确率 (%) 比较](https://github.com/bettermorn/IAICourse/assets/568965/fae4de7a-e011-4798-bb93-0fa484ca7285)
10代表性类别增量学习方法在 CIFAR-100 和 ImageNet-Sub 数据集上的性能比较  数据回放方法为 每个旧类别保存 10 个样本  从左到右依次为 5, 10 和 25 阶段增量学习设定
https://github.com/bettermorn/IAICourse/blob/main/img/10%E4%BB%A3%E8%A1%A8%E6%80%A7%E7%B1%BB%E5%88%AB%E5%A2%9E%E9%87%8F%E5%AD%A6%E4%B9%A0%E6%96%B9%E6%B3%95%E5%9C%A8%20CIFAR-100%20%E5%92%8C%20ImageNet-Sub%20%E6%95%B0%E6%8D%AE%E9%9B%86%E4%B8%8A%E7%9A%84%E6%80%A7%E8%83%BD%E6%AF%94%E8%BE%83.%20%E6%95%B0%E6%8D%AE%E5%9B%9E%E6%94%BE%E6%96%B9%E6%B3%95%E4%B8%BA%20%E6%AF%8F%E4%B8%AA%E6%97%A7%E7%B1%BB%E5%88%AB%E4%BF%9D%E5%AD%98%2010%20%E4%B8%AA%E6%A0%B7%E6%9C%AC.%20%E4%BB%8E%E5%B7%A6%E5%88%B0%E5%8F%B3%E4%BE%9D%E6%AC%A1%E4%B8%BA%205%2C%2010%20%E5%92%8C%2025%20%E9%98%B6%E6%AE%B5%E5%A2%9E%E9%87%8F%E5%AD%A6%E4%B9%A0%E8%AE%BE%E5%AE%9A.png
![10代表性类别增量学习方法在 CIFAR-100 和 ImageNet-Sub 数据集上的性能比较  数据回放方法为 每个旧类别保存 10 个样本  从左到右依次为 5, 10 和 25 阶段增量学习设定](https://github.com/bettermorn/IAICourse/assets/568965/e4f44d74-f2f7-4d3e-89fb-956e26aafd52)



