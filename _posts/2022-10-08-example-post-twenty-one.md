---

title: multi-model dialogue generation
categories:
- 论文精读
feature_image: "https://user-images.githubusercontent.com/53364734/192078882-190b1b14-a1ee-4590-ac1f-56ac81ffeb56.png"

---
开设一个新的专题，论文精读。然后总结多模态对话系统中的技术，发展现状，以及科研究的点。
<!-- more -->

更改链接：[![更改博客链接](https://user-images.githubusercontent.com/53364734/192180297-c1654533-eb5f-4bf9-aa9f-ab830208a5e3.png)](https://github.com/lizeyujack/lizeyujack.github.io/blob/main/_posts/2022-10-08-example-post-twenty-one.md)

multi-model vision-language数据集：COCO  [128],  VQA  [129],  Visual  Genome[130], SBU Captions [131], Cooking312K [7], LAIT [120], e-SNLI-VE [132], ARCH [133], Adversarial VQA [134], OTT-QA [16], MULTIMODALQA (MMQA) [135], VALUE [136],Fashion  IQ  [137],  LRS2-BBC  [138],  ActivityNet  [139],  CN-ERTA [140], DVD [141], VisDial [142], PhotoChat [143].

```bash
{%raw%}
@report{,
   abstract = {Natural language explanation (NLE) models aim at explaining the decision-making process of a black box system via generating natural language sentences which are human-friendly, high-level and fine-grained. Current NLE models 1 explain the decision-making process of a vision or vision-language model (a.k.a., task model), e.g., a VQA model, via a language model (a.k.a., explanation model), e.g., GPT. Other than the additional memory resources and inference time required by the task model, the task and explanation models are completely independent, which disas-sociates the explanation from the reasoning process made to predict the answer. We introduce NLX-GPT, a general , compact and faithful language model that can simultaneously predict an answer and explain it. We first conduct pre-training on large scale data of image-caption pairs for general understanding of images, and then formulate the answer as a text prediction task along with the explanation. Without region proposals nor a task model, our resulting overall framework attains better evaluation scores, contains much less parameters and is 15× faster than the current SoA model. We then address the problem of evaluating the explanations which can be in many times generic, data-biased and can come in several forms. We therefore design 2 new evaluation measures: (1) explain-predict and (2) retrieval-based attack, a self-evaluation framework that requires no labels. Code is at: https://github.com/fawazsammani/nlxgpt.},
   author = {Fawaz Sammani and Tanmoy Mukherjee and Nikos Deligiannis},
   title = {NLX-GPT: A Model for Natural Language Explanations in Vision and Vision-Language Tasks},
   url = {https://github.com/fawazsammani/nlxgpt.},
}
@article{Meng2020,
   abstract = {When humans converse, what a speaker will say next significantly depends on what he sees. Unfortunately, existing dialogue models generate dialogue utterances only based on preceding textual contexts, and visual contexts are rarely considered. This is due to a lack of a large-scale multi-module dialogue dataset with utterances paired with visual contexts. In this paper, we release \{\bf OpenViDial\}, a large-scale multi-module dialogue dataset. The dialogue turns and visual contexts are extracted from movies and TV series, where each dialogue turn is paired with the corresponding visual context in which it takes place. OpenViDial contains a total number of 1.1 million dialogue turns, and thus 1.1 million visual contexts stored in images. Based on this dataset, we propose a family of encoder-decoder models leveraging both textual and visual contexts, from coarse-grained image features extracted from CNNs to fine-grained object features extracted from Faster R-CNNs. We observe that visual information significantly improves dialogue generation qualities, verifying the necessity of integrating multi-modal features for dialogue learning. Our work marks an important step towards large-scale multi-modal dialogue learning.},
   author = {Yuxian Meng and Shuhe Wang and Qinghong Han and Xiaofei Sun and Fei Wu and Rui Yan and Jiwei Li},
   month = {12},
   title = {OpenViDial: A Large-Scale, Open-Domain Dialogue Dataset with Visual Contexts},
   url = {http://arxiv.org/abs/2012.15015},
   year = {2020},
}
@article{Wang2021,
   abstract = {Multi-modal dialog modeling is of growing interest. In this work, we propose frameworks to resolve a specific case of multi-modal dialog generation that better mimics multi-modal dialog generation in the real world, where each dialog turn is associated with the visual context in which it takes place. Specifically, we propose to model the mutual dependency between text-visual features, where the model not only needs to learn the probability of generating the next dialog utterance given preceding dialog utterances and visual contexts, but also the probability of predicting the visual features in which a dialog utterance takes place, leading the generated dialog utterance specific to the visual context. We observe significant performance boosts over vanilla models when the mutual dependency between text and visual features is modeled. Code is available at https://github.com/ShannonAI/OpenViDial.},
   author = {Shuhe Wang and Yuxian Meng and Xiaofei Sun and Fei Wu and Rongbin Ouyang and Rui Yan and Tianwei Zhang and Jiwei Li},
   month = {5},
   title = {Modeling Text-visual Mutual Dependency for Multi-modal Dialog Generation},
   url = {http://arxiv.org/abs/2105.14445},
   year = {2021},
}
@article{Sun2021,
   abstract = {Responsing with image has been recognized as an important capability for an intelligent conversational agent. Yet existing works only focus on exploring the multimodal dialogue models which depend on retrieval-based methods, but neglecting generation methods. To fill in the gaps, we first present a multimodal dialogue generation model, which takes the dialogue history as input, then generates a textual sequence or an image as response. Learning such a model often requires multimodal dialogues containing both texts and images which are difficult to obtain. Motivated by the challenge in practice, we consider multimodal dialogue generation under a natural assumption that only limited training examples are available. In such a low-resource setting, we devise a novel conversational agent, Divter, in order to isolate parameters that depend on multimodal dialogues from the entire generation model. By this means, the major part of the model can be learned from a large number of text-only dialogues and text-image pairs respectively, then the whole parameters can be well fitted using the limited training examples. Extensive experiments demonstrate our method achieves state-of-the-art results in both automatic and human evaluation, and can generate informative text and high-resolution image responses.},
   author = {Qingfeng Sun and Yujing Wang and Can Xu and Kai Zheng and Yaming Yang and Huang Hu and Fei Xu and Jessica Zhang and Xiubo Geng and Daxin Jiang},
   month = {10},
   title = {Multimodal Dialogue Response Generation},
   url = {http://arxiv.org/abs/2110.08515},
   year = {2021},
}
@article{Xu2022,
   abstract = {Transformer is a promising neural network learner, and has achieved great success in various machine learning tasks. Thanks to the recent prevalence of multimodal applications and big data, Transformer-based multimodal learning has become a hot topic in AI research. This paper presents a comprehensive survey of Transformer techniques oriented at multimodal data. The main contents of this survey include: (1) a background of multimodal learning, Transformer ecosystem, and the multimodal big data era, (2) a theoretical review of Vanilla Transformer, Vision Transformer, and multimodal Transformers, from a geometrically topological perspective, (3) a review of multimodal Transformer applications, via two important paradigms, i.e., for multimodal pretraining and for specific multimodal tasks, (4) a summary of the common challenges and designs shared by the multimodal Transformer models and applications, and (5) a discussion of open problems and potential research directions for the community.},
   author = {Peng Xu and Xiatian Zhu and David A. Clifton},
   month = {6},
   title = {Multimodal Learning with Transformers: A Survey},
   url = {http://arxiv.org/abs/2206.06488},
   year = {2022},
}
@report{,
   author = {Aishwarya Agrawal},
   title = {Vision-Language landscape before the Pretraining Era},
}
@report{Teney2022,
   author = {Damien Teney and Acl Tutorial},
   title = {Vision-Language Pretraining: Current Trends and the Future Part 3: Beyond statistical learning},
   year = {2022},
}
@report{Agrawal2022,
   author = {Aishwarya Agrawal and Damien Teney and Aida Nematzadeh},
   title = {Vision-Language Pretraining: Current Trends and the Future},
   url = {https://vlp-tutorial-acl2022.github.io/},
   year = {2022},
}
@report{,
   abstract = {We present ViLBERT (short for Vision-and-Language BERT), a model for learning task-agnostic joint representations of image content and natural language. We extend the popular BERT architecture to a multi-modal two-stream model, processing both visual and textual inputs in separate streams that interact through co-attentional transformer layers. We pretrain our model through two proxy tasks on the large, automatically collected Conceptual Captions dataset and then transfer it to multiple established vision-and-language tasks-visual question answering, visual commonsense reasoning, referring expressions, and caption-based image retrieval-by making only minor additions to the base architecture. We observe significant improvements across tasks compared to existing task-specific models-achieving state-of-the-art on all four tasks. Our work represents a shift away from learning groundings between vision and language only as part of task training and towards treating visual grounding as a pretrainable and transferable capability.},
   author = {Jiasen Lu and Dhruv Batra and Devi Parikh and Stefan Lee},
   title = {ViLBERT: Pretraining Task-Agnostic Visiolinguistic Representations for Vision-and-Language Tasks},
}
@article{Alayrac2022,
   abstract = {Building models that can be rapidly adapted to numerous tasks using only a handful of annotated examples is an open challenge for multimodal machine learning research. We introduce Flamingo, a family of Visual Language Models (VLM) with this ability. Flamingo models include key architectural innovations to: (i) bridge powerful pretrained vision-only and language-only models, (ii) handle sequences of arbitrarily interleaved visual and textual data, and (iii) seamlessly ingest images or videos as inputs. Thanks to their flexibility, Flamingo models can be trained on large-scale multimodal web corpora containing arbitrarily interleaved text and images, which is key to endow them with in-context few-shot learning capabilities. We perform a thorough evaluation of the proposed Flamingo models, exploring and measuring their ability to rapidly adapt to a variety of image and video understanding benchmarks. These include open-ended tasks such as visual question-answering, where the model is prompted with a question which it has to answer, captioning tasks, which evaluate the ability to describe a scene or an event, and close-ended tasks such as multiple choice visual question-answering. For tasks lying anywhere on this spectrum, we demonstrate that a single Flamingo model can achieve a new state of the art for few-shot learning, simply by prompting the model with task-specific examples. On many of these benchmarks, Flamingo actually surpasses the performance of models that are fine-tuned on thousands of times more task-specific data.},
   author = {Jean-Baptiste Alayrac and Jeff Donahue and Pauline Luc and Antoine Miech and Iain Barr and Yana Hasson and Karel Lenc and Arthur Mensch and Katie Millican and Malcolm Reynolds and Roman Ring and Eliza Rutherford and Serkan Cabi and Tengda Han and Zhitao Gong and Sina Samangooei and Marianne Monteiro and Jacob Menick and Sebastian Borgeaud and Andrew Brock and Aida Nematzadeh and Sahand Sharifzadeh and Mikolaj Binkowski and Ricardo Barreira and Oriol Vinyals and Andrew Zisserman and Karen Simonyan},
   month = {4},
   title = {Flamingo: a Visual Language Model for Few-Shot Learning},
   url = {http://arxiv.org/abs/2204.14198},
   year = {2022},
}
@article{Shuster2018,
   abstract = {To achieve the long-term goal of machines being able to engage humans in conversation, our models should captivate the interest of their speaking partners. Communication grounded in images, whereby a dialogue is conducted based on a given photo, is a setup naturally appealing to humans (Hu et al., 2014). In this work we study large-scale architectures and datasets for this goal. We test a set of neural architectures using state-of-the-art image and text representations, considering various ways to fuse the components. To test such models, we collect a dataset of grounded human-human conversations, where speakers are asked to play roles given a provided emotional mood or style, as the use of such traits is also a key factor in engagingness (Guo et al., 2019). Our dataset, Image-Chat, consists of 202k dialogues over 202k images using 215 possible style traits. Automatic metrics and human evaluations of engagingness show the efficacy of our approach; in particular, we obtain state-of-the-art performance on the existing IGC task, and our best performing model is almost on par with humans on the Image-Chat test set (preferred 47.7% of the time).},
   author = {Kurt Shuster and Samuel Humeau and Antoine Bordes and Jason Weston},
   month = {11},
   title = {Image Chat: Engaging Grounded Conversations},
   url = {http://arxiv.org/abs/1811.00945},
   year = {2018},
}
@report{,
   abstract = {Natural language explanation (NLE) models aim at explaining the decision-making process of a black box system via generating natural language sentences which are human-friendly, high-level and fine-grained. Current NLE models 1 explain the decision-making process of a vision or vision-language model (a.k.a., task model), e.g., a VQA model, via a language model (a.k.a., explanation model), e.g., GPT. Other than the additional memory resources and inference time required by the task model, the task and explanation models are completely independent, which disas-sociates the explanation from the reasoning process made to predict the answer. We introduce NLX-GPT, a general , compact and faithful language model that can simultaneously predict an answer and explain it. We first conduct pre-training on large scale data of image-caption pairs for general understanding of images, and then formulate the answer as a text prediction task along with the explanation. Without region proposals nor a task model, our resulting overall framework attains better evaluation scores, contains much less parameters and is 15× faster than the current SoA model. We then address the problem of evaluating the explanations which can be in many times generic, data-biased and can come in several forms. We therefore design 2 new evaluation measures: (1) explain-predict and (2) retrieval-based attack, a self-evaluation framework that requires no labels. Code is at: https://github.com/fawazsammani/nlxgpt.},
   author = {Fawaz Sammani and Tanmoy Mukherjee and Nikos Deligiannis},
   title = {NLX-GPT: A Model for Natural Language Explanations in Vision and Vision-Language Tasks},
   url = {https://github.com/fawazsammani/nlxgpt.},
}
@article{Sun2021,
   abstract = {Responsing with image has been recognized as an important capability for an intelligent conversational agent. Yet existing works only focus on exploring the multimodal dialogue models which depend on retrieval-based methods, but neglecting generation methods. To fill in the gaps, we first present a multimodal dialogue generation model, which takes the dialogue history as input, then generates a textual sequence or an image as response. Learning such a model often requires multimodal dialogues containing both texts and images which are difficult to obtain. Motivated by the challenge in practice, we consider multimodal dialogue generation under a natural assumption that only limited training examples are available. In such a low-resource setting, we devise a novel conversational agent, Divter, in order to isolate parameters that depend on multimodal dialogues from the entire generation model. By this means, the major part of the model can be learned from a large number of text-only dialogues and text-image pairs respectively, then the whole parameters can be well fitted using the limited training examples. Extensive experiments demonstrate our method achieves state-of-the-art results in both automatic and human evaluation, and can generate informative text and high-resolution image responses.},
   author = {Qingfeng Sun and Yujing Wang and Can Xu and Kai Zheng and Yaming Yang and Huang Hu and Fei Xu and Jessica Zhang and Xiubo Geng and Daxin Jiang},
   month = {10},
   title = {Multimodal Dialogue Response Generation},
   url = {http://arxiv.org/abs/2110.08515},
   year = {2021},
}
{%endraw%}
```
