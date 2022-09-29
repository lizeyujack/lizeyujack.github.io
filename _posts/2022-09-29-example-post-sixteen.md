---

title: 没有属鼠的一天
categories:
- Academic
feature_image: "https://user-images.githubusercontent.com/53364734/191680041-3352d56c-bf95-4fe7-b917-5a07bdb7621d.png"

---

<!-- more -->


更改链接：[![更改博客链接](https://user-images.githubusercontent.com/53364734/192180297-c1654533-eb5f-4bf9-aa9f-ab830208a5e3.png)](https://github.com/lizeyujack/lizeyujack.github.io/edit/main/_posts/2022-09-29-example-post-sixteen.md)
- error1:
```
a        torch.Size([1, 84, 128])
a        torch.Size([1, 84, 128])
embed_q torch.Size([1, 1, 1, 128])
hidden   torch.Size([1, 1, 1, 128])
  0%|                                                                                                                                                                           | 0/9982 [00:00<?, ?it/s]
Traceback (most recent call last):
  File "train.py", line 49, in <module>
    model.train(data, int(args['clip']), reset=(i==0))
  File "/cluster/home/lizeyu/nsnet_bert/jack/NS-Dial-master/models/LTHR.py", line 199, in train
    kb_arr_plain)
  File "/cluster/home/lizeyu/anaconda3/envs/torch/lib/python3.7/site-packages/torch/nn/modules/module.py", line 727, in _call_impl
    result = self.forward(*input, **kwargs)
  File "/cluster/home/lizeyu/nsnet_bert/jack/NS-Dial-master/models/ReasonDecoder.py", line 44, in forward
    _, hidden = self.rnn(embed_q, hidden)### ??????
  File "/cluster/home/lizeyu/anaconda3/envs/torch/lib/python3.7/site-packages/torch/nn/modules/module.py", line 727, in _call_impl
    result = self.forward(*input, **kwargs)
  File "/cluster/home/lizeyu/anaconda3/envs/torch/lib/python3.7/site-packages/torch/nn/modules/rnn.py", line 737, in forward
    self.check_forward_args(input, hx, batch_sizes)
  File "/cluster/home/lizeyu/anaconda3/envs/torch/lib/python3.7/site-packages/torch/nn/modules/rnn.py", line 199, in check_forward_args
    self.check_input(input, batch_sizes)
  File "/cluster/home/lizeyu/anaconda3/envs/torch/lib/python3.7/site-packages/torch/nn/modules/rnn.py", line 176, in check_input
    expected_input_dim, input.dim()))
RuntimeError: input must have 3 dimensions, got 4
```

- decoder:

```python
for t in range(max_target_length):
            embed_q = self.dropout_layer(self.C(decoder_input))  # b * e 

            embed_q = embed_q.unsqueeze(0)
            hidden = hidden.squeeze(0)
            print('embed_q',embed_q.shape)# 1*128
            print('hidden\t',hidden.shape)
            if len(embed_q.size()) == 1: embed_q = embed_q.unsqueeze(0)
            _, hidden = self.rnn(embed_q, hidden)### ??????

            p_vocab = self.attend_vocab(self.C.weight, hidden.squeeze(0))
            all_decoder_outputs_vocab[t] = p_vocab
            _, topvi = p_vocab.data.topk(1)  # topvi: [batch_size * 1]

            # query question generator and reasoner using hidden state
            structure_type_logits, structure_type_action, structure_type_loss, \
            query_entity_h_logits, query_entity_h_action, query_entity_h_loss, \
            query_entity_t_logits, query_entity_t_action, query_entity_t_loss, candidates_prob, candidates_prob_logits = question_generator(context_arr, context_arr_lengths, hidden.squeeze(0), global_pointer, True)
            all_candidate_prob[t] = candidates_prob_logits
```
