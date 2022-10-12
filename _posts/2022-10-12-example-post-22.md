---

title: Generative response dialogue based on Photochat
categories:
- 论文精读
feature_image: "https://user-images.githubusercontent.com/53364734/192078882-190b1b14-a1ee-4590-ac1f-56ac81ffeb56.png"

---
 Multimodal Dialogue Response Generation 论文精读:
<!-- more -->

更改链接：[![更改博客链接](https://user-images.githubusercontent.com/53364734/192180297-c1654533-eb5f-4bf9-aa9f-ab830208a5e3.png)](https://github.com/lizeyujack/lizeyujack.github.io/edit/main/_posts/2022-10-12-example-post-22.md)



```python
{%raw%}
from sacred import Experiment
{%endraw%}
```

sacred可以用来调整参数进行输出测试：

Multimodal Dialogue Response Generation

黄民烈：对话系统要尽量避免万能回复（I don't know）

图像响应已被公认为智能会话代理的一项重要功能。现有的研究只关注基于检索方法的多模态对话模型的探索，而忽略了生成方法。为了填补空白，我们首先提出了一个新的任务:在给定对话上下文的情况下，一个模型需要生成文本或图像作为响应。学习这样的MDRG模型通常需要包含文本和图像的多模态对话，这是很难获得的。由于实践中的挑战，我们考虑MDRG时自然假设只有有限的训练示例可用。在这种低资源设置下，我们设计了一个新的会话代理Divter，以便从整个生成模型中分离依赖于多模态对话的参数。通过这种方法，可以分别从大量纯文本对话和文本图像对中学习模型的主要部分，然后只用少量的训练示例就可以很好地拟合整个参数。大量的实验表明，我们的方法在自动和人工评价方面都达到了最先进的结果，并可以生成信息丰富的文本和高分辨率的图像响应 .



PhotoChat数据集提出一种基于检索的方法来解决上述挑战。然而，基于检索的方法的性能在特定领域受到预先构建的会话历史存储库的大小的限制，特别是对于历史中没有覆盖的长尾上下文，其中检索系统的图像响应集也是固定的。另一方面，更好的方法是相应地生成一个新的。

In this paper, we formulate a new problem: Multimodal Dialogue Response Generation(MDRG), that is, given the dialogue context, the model should not only generate a pure text response but also have the capacity to generate a multimodal response.


![image](https://user-images.githubusercontent.com/53364734/195272283-3c736500-af6f-4189-815a-17b479007c50.png)



## Citation
> Multimodal Dialogue Response Generation (Sun et al., ACL 2022)
