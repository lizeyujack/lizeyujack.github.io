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
