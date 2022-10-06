---

title: 女票发工资，普天同庆！
categories:
- Academic
feature_image: "https://user-images.githubusercontent.com/53364734/192078882-190b1b14-a1ee-4590-ac1f-56ac81ffeb56.png"

---
An Interpretable Neuro-Symbolic Reasoning Framework forTask-Oriented Dialogue Generation 论文的原始代码已经恢复，目前正在训练。
就怕是作者心里有鬼，然后有问题。
<!-- more -->


更改链接：[![更改博客链接](https://user-images.githubusercontent.com/53364734/192180297-c1654533-eb5f-4bf9-aa9f-ab830208a5e3.png)](https://github.com/lizeyujack/lizeyujack.github.io/edit/main/_posts/2022-10-05-example-post-twentity.md)

- 交大硕士国奖得住：
战略上的懒惰，很难用战术上的努力去弥补。路线不对，知识越多越繁重。
相信自己可以取得好的结果。战略上藐视敌人，战术上重视敌人。
1. 保持自信
2. 一定要稳，稳中求进
3. 避免内耗
4. 精神上有自己的想法，不轻易的被他人的评价所影响。（重点号）
5. 有一项爱好（值得坚持的：健身、游戏【原神？】）派遣消极情绪。
6. 珍惜时间
7. 精益求精，有毅力，永不放弃
8. 选择大于努力（平台的重要性）
9. 投稿，拒稿，不能颓废、气馁
10. 文献的共同点和差异性（创新性）
11. 在实践中发现问题（看问题比较多的时候），case study
12. 时间管理，okr工作法、甘特图
13. 工作日志。汇报进度
14. 年计划。月计划。周计划。每天要干什么。下周要做什么？下个月要做什么？
15. 终点日期的标记
16. 积极保持同学与老师的交流。（不同学校，不同专业）
17. 学会适应导师，而不是导师适应自己
18. 有一个好心情。劳逸结合。好心情-》才会有好的科研
19. 总压抑会出问题
20. 个人简介多放亮点与特色，让专家好抓重点。
21. 背景介绍要和科研结合（1页）+工作是有意义的

```python
{%raw%} 
import torch
import torch.nn as nn
from utils.config import *
from utils.utils_general import _cuda
import random
from transformers.tokenization_bert import BertTokenizer
from transformers.modeling_bert import BertModel
import sys
BERT_PRETRAINED_MODEL = 'bert-base-uncased'

class Encoder(nn.Module):
    def __init__(self, input_size, hidden_size, dropout, vocab, embedding_dim, lang, n_layers=1):
        super(Encoder, self).__init__()
        self.name = "Encoder"

        self.input_size = input_size
        self.hidden_size = hidden_size
        self.dropout = dropout
        self.n_layers = n_layers
        self.vocab = vocab
        self.embedding_dim = embedding_dim
        self.lang = lang

        self.dropout_layer = nn.Dropout(dropout)
        self.embedding = nn.Embedding(input_size, hidden_size, padding_idx=PAD_token)
        self.gru = nn.GRU(hidden_size, hidden_size, n_layers, dropout=dropout, bidirectional=True)
        self.W = nn.Linear(2*hidden_size, hidden_size)
        self.W = nn.Linear(768, hidden_size)
        self.tokenizer = BertTokenizer.from_pretrained(BERT_PRETRAINED_MODEL,
                                                       do_lower_case=bool(BERT_PRETRAINED_MODEL.endswith("uncased")))
        self.bert = BertModel.from_pretrained(BERT_PRETRAINED_MODEL)

    def get_state(self, bsz):
        """Get cell states and hidden states."""
        return _cuda(torch.zeros(2, bsz, self.hidden_size))

    def get_state(self, bsz):
        """Get cell states and hidden states."""
        return _cuda(torch.zeros(2, bsz, self.hidden_size))

    def trunc_seq(self, tokens, max_num_tokens):
        """Truncates a pair of sequences to a maximum sequence length. Lifted from Google's BERT repo."""
        l = 0
        r = len(tokens)
        trunc_tokens = list(tokens)
        while r - l > max_num_tokens:
            if random.random() < 0.5:
                l += 1
            else:
                r -= 1
        return trunc_tokens[l:r]

    def compute_bert_input(self, conv_arr_plain, batch_size,MAX_INPUT_LEN):
        bert_input = ["".join(elm) for elm in conv_arr_plain]
        lens = [len(ele.split(" ")) for ele in bert_input]
        max_len = max(lens)
        padded_seqs = torch.zeros(batch_size, min(max_len, MAX_INPUT_LEN)).long()
        input_mask = torch.zeros(batch_size, min(max_len, MAX_INPUT_LEN))
        for i, seq in enumerate(bert_input):
            end = min(lens[i], MAX_INPUT_LEN
            tokens = self.tokenizer.tokenize(seq)
            tokens = self.trunc_seq(tokens, 512)
            seq_id = self.tokenizer.convert_tokens_to_ids(tokens)
            padded_seqs[i, :end] = torch.Tensor(seq_id[:end])
            input_mask[i, :end] = 1
        return _cuda(padded_seqs), _cuda(input_mask)

    def forward(self, conv_arr_plain,input_seqs, input_lengths):
        # - Encode Dialogue History
        # BERT Encoder
        batch_size = int(args['batch'])
        input_ids, input_mask = self.compute_bert_input(conv_arr_plain, batch_size,input_lengths[0])
        _, pooled_output = self.bert(input_ids, attention_mask=input_mask)
        encoded_hidden = self.W(pooled_output)
        encoded_hidden = encoded_hidden.unsqueeze(0)
        return encoded_hidden
{%endraw%}
```
- eight minutes to go:
![image](https://user-images.githubusercontent.com/53364734/194055373-4a6a6025-e987-4274-b226-cfdc4e267b65.png)

## 帕累托原则：
<video id="video-share_html5_api" class="vjs-tech" tabindex="-1" preload="auto" src="https://560-cn-east-2.cdn-vod.huaweicloud.com/asset/a7dcecdf8f9c4cb6c99187156cd2bd46/ff727aaee49ad19ae4d4214d699d1801.mp4?auth_info=m0Np1R8LtIfXrX3afUh%2FRDBIctx%2FrxhBjA%2F3C4eDM4ZlK3d3tsYuSFiCAnm05WOCIsWTbEXvxDVDhslRgngW2Q%3D%3D.95735b1617edcb585f43536218da6d05"></video>

