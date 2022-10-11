---

title: Vision Language model, based on chat
categories:
- 论文精读
feature_image: "https://user-images.githubusercontent.com/53364734/192078882-190b1b14-a1ee-4590-ac1f-56ac81ffeb56.png"

---
PhotoChat 论文精读:
<!-- more -->

更改链接：[![更改博客链接](https://user-images.githubusercontent.com/53364734/192180297-c1654533-eb5f-4bf9-aa9f-ab830208a5e3.png)](https://github.com/lizeyujack/lizeyujack.github.io/edit/main/_posts/2022-10-11-example-post-21.md)

## ACL2021：PhotoChat: A Human-Human Dialogue Dataset with Photo Sharing Behavior for Joint Image-Text Modeling

本文提出了一个新的人际对话数据集- PhotoChat，这是第一个阐明在线消息传递中的照片共享行为的数据集。PhotoChat包含12k个对话，每个对话都配有一张用户照片，在对话过程中共享。基于该数据集，我们提出了两个任务以促进图像-文本建模的研究:
1. 一个是预测一个人是否打算在下一次对话中分享照片的照片分享意图预测任务，（intent identification）
2. 另一个是根据对话上下文检索最相关的照片的照片检索任务。(image retrieval)

本文创建了PhotoChat—一个人与人对话数据集，其中一张照片在对话过程中由一人分享给另一人。据我们所知，这是第一个捕捉照片分享活动的数据集。我们从OpenImage V4数据集(Kuznetsova et al.， 2020)中选择图片作为共享照片，并使用众包插件生成12286个对话，平均每个对话10次。在对话收集过程中，照片只对被指示共享照片的一方可见，在共享后对双方都可见。基于收集到的数据集，我们提出了构建照片建议系统的两个关键任务:照片分享意图预测任务(预测一个人是否打算在下一个对话对话中分享照片)和基于对话的图像检索任务(在给定的对话上下文中检索最相关的照片)。对于两者，我们建立基线模型，报告和分析它们的性能。最佳的照片共享意图预测基线模型F1得分为58.1%，准确率为58.2%，查全率为57.9%。最好的交叉注意图像检索模型达到10.4% recall@1 / 1000个候选。我们还提出了一种利用对象标签对图像特征进行编码的双编码器模型，该模型在没有交叉注意机制的所有模型中达到了最佳性能。


> 可惜PhotoChat不适合作为dialogue generation。注重检索和意图预测。

$\sigma$
<img src="http://latex.codecogs.com/gif.latex?c=\sqrt{a^2+b^2}\sigma" alt="" border="0" align="middle" />


对于意图识别：本文为了建立基线，我们微调了三个SOTA预先训练的模型——BERT、ALBERT  and T5.
{% include latex.html latex="P = \{p_1, p_2, ..., p_M\}" %}
