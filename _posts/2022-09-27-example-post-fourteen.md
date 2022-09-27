---

title: 跑通[NS_dial](https://github.com/shiquanyang/NS-Dial)的一天。
categories:
- Academic
feature_image: "https://user-images.githubusercontent.com/53364734/192078882-190b1b14-a1ee-4590-ac1f-56ac81ffeb56.png"

---
把embeded的东西搞出来了。可是遇到了OOM。
<!-- more -->

更改链接：[![更改博客链接](https://user-images.githubusercontent.com/53364734/192180297-c1654533-eb5f-4bf9-aa9f-ab830208a5e3.png)](https://github.com/lizeyujack/lizeyujack.github.io/edit/main/_posts/2022-09-27-example-post-fourteen.md)

## 编码之后的输出。对于multiwoz数据集是这样的。
```
{%raw%}(torch) [lizeyu@head2 NS-Dial]$ CUDA_VISIBLE_DEVICES=3 python train.py -ds=multiwoz -bsz=1 -hdd=128 -lr=0.001 -dr=0.2 -evalp=10 -max_neg_cnt=5 -max_depth=3
{'dataset': 'multiwoz', 'task': '', 'decoder': None, 'hidden': '128', 'batch': '1', 'learn': '0.001', 'drop': '0.2', 'unk_mask': 1, 'layer': None, 'limit': -10000, 'path': None, 'clip': 10, 'teacher_forcing_ratio': 0.5, 'sample': None, 'evalp': '10', 'addName': '', 'genSample': 0, 'earlyStop': 'BLEU', 'ablationG': 0, 'ablationH': 0, 'record': 0, 'reverse_graph': 0, 'max_deps': 3, 'ablationD': 0, 'maxhops': 3, 'graphhdd': 8, 'nheads': 8, 'alpha': 0.2, 'graph_dr': 0.6, 'graph_layer': 1, 'max_depth': 3, 'max_neg_cnt': 5, 'show_trees': 0}
USE_CUDA: True
Reading lines from /cluster/home/lizeyu/NS-Dial/data/multiwoz/train.txt
Reading lines from /cluster/home/lizeyu/NS-Dial/data/multiwoz/valid.txt
Reading lines from /cluster/home/lizeyu/NS-Dial/data/multiwoz/test.txt
Read 9982 sentence pairs train
Read 734 sentence pairs dev
Read 859 sentence pairs test
Vocab_size: 6334 
Max. length of system response: 55 
USE_CUDA=True
/cluster/home/lizeyu/anaconda3/envs/torch/lib/python3.7/site-packages/torch/nn/modules/rnn.py:61: UserWarning: dropout option adds dropout after all but last recurrent layer, so non-zero dropout expects num_layers greater than 1, but got dropout=0.2 and num_layers=1
  "num_layers={}".format(dropout, num_layers))
Epoch:0
  0%|                                                                                                                                                                           | 0/9982 [00:00<?, ?it/s]['are there any restaurants serving middle eastern food ?'] torch.Size([9, 1, 4])
embedded 1       torch.Size([9, 4, 128])
embedded 2       torch.Size([9, 1, 4, 128])
embedded 3       torch.Size([9, 1, 128])
hidden out size: 4       torch.Size([2, 1, 128])
hid      5 torch.Size([1, 1, 128])
encode   torch.Size([1, 128])
  0%|                                                                                                                                                                           | 0/9982 [00:00<?, ?it/s]
(torch) [lizeyu@head2 NS-Dial]$ CUDA_VISIBLE_DEVICES=3 python train.py -ds=multiwoz -bsz=1 -hdd=128 -lr=0.001 -dr=0.2 -evalp=10 -max_neg_cnt=5 -max_depth=3
{'dataset': 'multiwoz', 'task': '', 'decoder': None, 'hidden': '128', 'batch': '1', 'learn': '0.001', 'drop': '0.2', 'unk_mask': 1, 'layer': None, 'limit': -10000, 'path': None, 'clip': 10, 'teacher_forcing_ratio': 0.5, 'sample': None, 'evalp': '10', 'addName': '', 'genSample': 0, 'earlyStop': 'BLEU', 'ablationG': 0, 'ablationH': 0, 'record': 0, 'reverse_graph': 0, 'max_deps': 3, 'ablationD': 0, 'maxhops': 3, 'graphhdd': 8, 'nheads': 8, 'alpha': 0.2, 'graph_dr': 0.6, 'graph_layer': 1, 'max_depth': 3, 'max_neg_cnt': 5, 'show_trees': 0}
USE_CUDA: True
Reading lines from /cluster/home/lizeyu/NS-Dial/data/multiwoz/train.txt
Reading lines from /cluster/home/lizeyu/NS-Dial/data/multiwoz/valid.txt
Reading lines from /cluster/home/lizeyu/NS-Dial/data/multiwoz/test.txt
Read 9982 sentence pairs train
Read 734 sentence pairs dev
Read 859 sentence pairs test
Vocab_size: 6334 
Max. length of system response: 55 
USE_CUDA=True
/cluster/home/lizeyu/anaconda3/envs/torch/lib/python3.7/site-packages/torch/nn/modules/rnn.py:61: UserWarning: dropout option adds dropout after all but last recurrent layer, so non-zero dropout expects num_layers greater than 1, but got dropout=0.2 and num_layers=1
  "num_layers={}".format(dropout, num_layers))
Epoch:0
  0%|                                                                                                                                                                           | 0/9982 [00:00<?, ?it/s]['i am looking for an expensive restaurant in the south part of town'] torch.Size([13, 1, 4])
embedded 1       torch.Size([13, 4, 128])
embedded 2       torch.Size([13, 1, 4, 128])
embedded 3       torch.Size([13, 1, 128])
hidden out size: 4       torch.Size([2, 1, 128])
hid      5 torch.Size([1, 1, 128])
encode   torch.Size([1, 128])
L:20.62, LV:14.18, LG:1.59, LCA:4.73, LRE:0.12:   0%|                                                                                                                 | 1/9982 [00:01<4:11:18,  1.51s/it]['i want to find a place to stay in the north with free parking'] torch.Size([14, 1, 4])
embedded 1       torch.Size([14, 4, 128])
embedded 2       torch.Size([14, 1, 4, 128])
embedded 3       torch.Size([14, 1, 128])
hidden out size: 4       torch.Size([2, 1, 128])
hid      5 torch.Size([1, 1, 128])
encode   torch.Size([1, 128])
L:19.50, LV:13.95, LG:1.26, LCA:4.17, LRE:0.13:   0%|                                                                                                                 | 2/9982 [00:06<6:42:12,  2.42s/it]['please find a train that departs from peterborough and arrives in cambridge by 8:45 okay and which day would you like to travel ? i would like to leave on saturday from london_liverpool_street the tr3390 arrives saturday at 8:38 would you like me to book it for you ? can i get travel time and price first please ? the trip is 50_minutes long and it is 13.20_pounds for a ticket ok thanks im ready to book great i have booked your ticket your reference number is : 9llwmnom may i help with anything further i m so sorry i didn t mean to book yet i won t need that reservation could you make sure that train tr3390 is departing from london liverpool ? train tr3390 is departing from peterborough to cambridge would you like me to look for a train departing from london liverpool ? yes please i need to know the price and travel time for that as well'] torch.Size([162, 1, 4])
embedded 1       torch.Size([162, 4, 128])
embedded 2       torch.Size([162, 1, 4, 128])
embedded 3       torch.Size([162, 1, 128])
hidden out size: 4       torch.Size([2, 1, 128])
hid      5 torch.Size([1, 1, 128])
encode   torch.Size([1, 128])
L:20.01, LV:14.27, LG:1.16, LCA:4.45, LRE:0.13:   0%|                                                                                                                 | 3/9982 [00:10<8:15:46,  2.98s/it]['i want a restaurant in the south part of town and serves panasian food sorry there are no restaurants in the south part of town serving panasian food italian food please phone number and postcode please frankie_and_bennys serves italian food in the south part of town the phone number is 01223 412430 and the postcode is c.b 1 7 dy sorry what type of food do they serve ? they serve italian food what is the price range ?'] torch.Size([79, 1, 4])
embedded 1       torch.Size([79, 4, 128])
embedded 2       torch.Size([79, 1, 4, 128])
embedded 3       torch.Size([79, 1, 128])
hidden out size: 4       torch.Size([2, 1, 128])
hid      5 torch.Size([1, 1, 128])
encode   torch.Size([1, 128])
L:20.30, LV:15.00, LG:1.13, LCA:4.04, LRE:0.13:   0%|                                                                                                                 | 4/9982 [00:11<6:29:26,  2.34s/it]['i m looking for cheap lodgings alexander_bed_and_breakfast is an option it is located at 56_saint_barnabas_road what s it s star rating ? it has a 4 star rating would you like me to book a room for you ? yes i need it for four people and five nights what day do you want that booking to start ? i need it to start thursday night and once it is booked can you send me the reference number ?'] torch.Size([79, 1, 4])
embedded 1       torch.Size([79, 4, 128])
embedded 2       torch.Size([79, 1, 4, 128])
embedded 3       torch.Size([79, 1, 128])
hidden out size: 4       torch.Size([2, 1, 128])
hid      5 torch.Size([1, 1, 128])
encode   torch.Size([1, 128]){%endraw%}```
- 彩蛋：

{% include video.html id="19N4119729" t="0" title="Siteleaf tutorial video" %}
