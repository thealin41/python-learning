# 基本原理
持续学习(Continual Learning)算法试图为神经网络实现像人们一样学习大量不同的任务，不出现任何负面的相互干扰， 并解决灾难性的遗忘问题。持续学习算法的重点不是如何利用在以前任务中学到的知识来帮助更好地学习新任务，而是解决灾难性遗忘的问题。

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
# 

