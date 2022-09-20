---
title: 科研整理，预计明天解封
categories:
- Academic
feature_image: "![2022-9-20-6-54_acc](https://user-images.githubusercontent.com/53364734/191151928-915b9d30-b0cf-46d5-aed9-f85d0f493bda.jpg)
"
---
zhongchuan的效果显著。5分类准确率99/[validation cases](https://github.com/lizeyujack/lizeyujack.github.io/files/9603466/2022-9-20-6-54_0.99_.csv)
<!-- more -->
1. TA： 微电子系统综合设计课程。(实验1/2)|done
2. 继续复现NeRF文章: CVPR oral present:[this one](https://bmild.github.io/rawnerf/)|done 1/2


The calculation resources are pretty tight for the whole members of ICAT. Further, we will have more and more cards there.
![image](https://user-images.githubusercontent.com/53364734/191153638-deba7363-b88e-4f62-a41c-f362638b8978.png)
Acc plot pic in here:

![2022-9-20-6-54_acc](https://user-images.githubusercontent.com/53364734/191191426-0c99ae51-3afd-48aa-aed6-91746bc507f5.jpg)


- Today's site:
```
@article{Eric2019,
   abstract = {MultiWOZ 2.0 (Budzianowski et al., 2018) is a recently released multi-domain dialogue dataset spanning 7 distinct domains and containing over 10,000 dialogues. Though immensely useful and one of the largest resources of its kind to-date, MultiWOZ 2.0 has a few shortcomings. Firstly, there is substantial noise in the dialogue state annotations and dialogue utterances which negatively impact the performance of state-tracking models. Secondly, follow-up work (Lee et al., 2019) has augmented the original dataset with user dialogue acts. This leads to multiple co-existent versions of the same dataset with minor modifications. In this work we tackle the aforementioned issues by introducing MultiWOZ 2.1. To fix the noisy state annotations, we use crowdsourced workers to re-annotate state and utterances based on the original utterances in the dataset. This correction process results in changes to over 32% of state annotations across 40% of the dialogue turns. In addition, we fix 146 dialogue utterances by canonicalizing slot values in the utterances to the values in the dataset ontology. To address the second problem, we combined the contributions of the follow-up works into MultiWOZ 2.1. Hence, our dataset also includes user dialogue acts as well as multiple slot descriptions per dialogue state slot. We then benchmark a number of state-of-the-art dialogue state tracking models on the MultiWOZ 2.1 dataset and show the joint state tracking performance on the corrected state annotations. We are publicly releasing MultiWOZ 2.1 to the community, hoping that this dataset resource will allow for more effective models across various dialogue subproblems to be built in the future.},
   author = {Mihail Eric and Rahul Goel and Shachi Paul and Adarsh Kumar and Abhishek Sethi and Anuj Kumar Goyal and Peter Ku and Sanchit Agarwal and Shuyang Gao and Dilek Hakkani-T},
   isbn = {1907.01669v4},
   keywords = {conversational,dialogue,dialogue act,end-to-end,multi-domain,state tracking},
   title = {MultiWOZ 2.1: A Consolidated Multi-Domain Dialogue Dataset with State Corrections and State Tracking Baselines},
   year = {2019},
}
@article{Liu2022,
   abstract = {Existing knowledge-grounded dialogue systems typically use finetuned versions of a pretrained language model (LM) and large-scale knowledge bases. These models typically fail to generalize on topics outside of the knowledge base, and require maintaining separate potentially large checkpoints each time finetuning is needed. In this paper, we aim to address these limitations by leveraging the inherent knowledge stored in the pretrained LM as well as its powerful generation ability. We propose a multi-stage prompting approach to generate knowledgeable responses from a single pretrained LM. We first prompt the LM to generate knowledge based on the dialogue context. Then, we further prompt it to generate responses based on the dialogue context and the previously generated knowledge. Results show that our knowledge generator outperforms the state-of-the-art retrieval-based model by 5.8% when combining knowledge relevance and correctness. In addition, our multi-stage prompting outperforms the finetuning-based dialogue model in terms of response knowledgeability and engagement by up to 10% and 5%, respectively. Furthermore, we scale our model up to 530 billion parameters and show that larger LMs improve the generation correctness score by up to 10%, and response relevance, knowledgeability and engagement by up to 10%. Our code is available at: https://github.com/NVIDIA/Megatron-LM.},
   author = {Zihan Liu and Mostofa Patwary and Ryan Prenger and Shrimai Prabhumoye and Wei Ping and Mohammad Shoeybi and Bryan Catanzaro},
   month = {3},
   title = {Multi-Stage Prompting for Knowledgeable Dialogue Generation},
   url = {http://arxiv.org/abs/2203.08745},
   year = {2022},
}
@article{Cao2022,
   abstract = {Towards building intelligent dialogue agents, there has been a growing interest in introducing explicit personas in generation models. However, with limited persona-based dialogue data at hand, it may be difficult to train a dialogue generation model well. We point out that the data challenges of this generation task lie in two aspects: first, it is expensive to scale up current persona-based dialogue datasets; second, each data sample in this task is more complex to learn with than conventional dialogue data. To alleviate the above data issues, we propose a data manipulation method, which is model-agnostic to be packed with any persona-based dialogue generation model to improve its performance. The original training samples will first be distilled and thus expected to be fitted more easily. Next, we show various effective ways that can diversify such easier distilled data. A given base model will then be trained via the constructed data curricula, i.e. first on augmented distilled samples and then on original ones. Experiments illustrate the superiority of our method with two strong base dialogue models (Transformer encoder-decoder and GPT2).},
   author = {Yu Cao and Wei Bi and Meng Fang and Shuming Shi and Dacheng Tao},
   month = {4},
   title = {A Model-Agnostic Data Manipulation Method for Persona-based Dialogue Generation},
   url = {http://arxiv.org/abs/2204.09867},
   year = {2022},
}
@article{,
   abstract = {Recent studies have shown remarkable success in end-to-end task-oriented dialog system. However, most neural models rely on large training data, which are only available for a certain number of task domains, such as navigation and scheduling. This makes it difficult to scalable for a new domain with limited labeled data. However, there has been relatively little research on how to effectively use data from all domains to improve the performance of each domain and also unseen domains. To this end, we investigate methods that can make explicit use of domain knowledge and introduce a shared-private network to learn shared and specific knowledge. In addition, we propose a novel Dynamic Fusion Network (DF-Net) which automatically exploit the relevance between the target domain and each domain. Results show that our model outperforms existing methods on multi-domain dialogue, giving the state-of-the-art in the literature. Besides, with little training data, we show its transfer-ability by outperforming prior best model by 13.9% on average.},
   author = {Libo Qin and Xiao Xu and Wanxiang Che and Yue Zhang and Ting Liu},
   title = {Dynamic Fusion Network for Multi-Domain End-to-end Task-Oriented Dialog},
   url = {https://github.com/LooperXX/DF-Net.},
}
```

{% include map.html id="14BzLad2HHz_NlaAFaV7BeQ-neBpp-gs&ll=31.110131760085135%2C121.4370075&z=12" title="Coffee shop map" %}
