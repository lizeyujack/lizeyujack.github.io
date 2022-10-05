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
            # We want to sometimes truncate from the front and sometimes from the
            # back to add more randomness and avoid biases.
            if random.random() < 0.5:
                l += 1
            else:
                r -= 1
        return trunc_tokens[l:r]

    def compute_bert_input(self, conv_arr_plain, batch_size,MAX_INPUT_LEN):
        # convert to id and padding
        # print("max\t",MAX_INPUT_LEN)
        bert_input = ["".join(elm) for elm in conv_arr_plain]
        # print('bert_input\t',bert_input)
        lens = [len(ele.split(" ")) for ele in bert_input]
        # print('lens\t',lens)
        max_len = max(lens)
        padded_seqs = torch.zeros(batch_size, min(max_len, MAX_INPUT_LEN)).long()
        input_mask = torch.zeros(batch_size, min(max_len, MAX_INPUT_LEN))
        # print('padded_seqs\t',padded_seqs.shape)
        for i, seq in enumerate(bert_input):
            end = min(lens[i], MAX_INPUT_LEN)
            # print(seq)
            # print('end\t',end)
            tokens = self.tokenizer.tokenize(seq)
            tokens = self.trunc_seq(tokens, 512)
            # print(tokens)
            seq_id = self.tokenizer.convert_tokens_to_ids(tokens)
            # print('seq_id\t',len(seq_id))
            padded_seqs[i, :end] = torch.Tensor(seq_id[:end])
            input_mask[i, :end] = 1
        return _cuda(padded_seqs), _cuda(input_mask)

    def forward(self, conv_arr_plain,input_seqs, input_lengths):
        # - Encode Dialogue History
        # BERT Encoder
        # print('input_seqs',input_seqs)
        # sys.exit()
        # batch_size = input_seqs.size(0)
        batch_size = int(args['batch'])
        # print('seq\t',conv_arr_plain)
        input_ids, input_mask = self.compute_bert_input(conv_arr_plain, batch_size,input_lengths[0])
        # print('input_ids',input_ids.shape)
        # print(input_ids.shape,input_mask.shape)
        # sys.exit()
        _, pooled_output = self.bert(input_ids, attention_mask=input_mask)
        # print(pooled_output.shape)
        encoded_hidden = self.W(pooled_output)
        # print('ot\t',encoded_hidden.shape)
        # encoded_hidden = torch.sum(encoded_hidden,0)
        # print(encoded_hidden.shape)
        # sys.exit()
        # embedded = self.embedding(input_seqs.contiguous().view(input_seqs.size(0), -1).long())
        # print(embedded.shape)
        # embedded = embedded.view(input_seqs.size()+(embedded.size(-1),))
        # embedded = torch.sum(embedded, 2).squeeze(2)
        # embedded = self.dropout_layer(embedded)
        # hidden = self.get_state(input_seqs.size(1))
        # print("input_seqs out size: ", input_seqs.size())
        # print("embedded size: ", embedded.size())
        # if input_lengths:
        #     embedded = nn.utils.rnn.pack_padded_sequence(embedded, input_lengths, batch_first=False)
        # outputs, hidden = self.gru(embedded, hidden)
        # if input_lengths:
        #    outputs, _ = nn.utils.rnn.pad_packed_sequence(outputs, batch_first=False)
        # hidden = self.W(torch.cat((hidden[0], hidden[1]), dim=1)).unsqueeze(0)
        # outputs = self.W(outputs)
        # print(hidden.shape)
        # print("shape is \t",encoded_hidden.shape)
        encoded_hidden = encoded_hidden.unsqueeze(0)
        # print(encoded_hidden.shape)
        # print(encoded_hidden.shape)
        # sys.exit()
        return encoded_hidden
        

{%endraw%}
```
- eight minutes to go:
![image](https://user-images.githubusercontent.com/53364734/194055373-4a6a6025-e987-4274-b226-cfdc4e267b65.png)
