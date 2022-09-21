---
title: 如何使用服务器
categories:
- Academic
feature_image: ""
---
😒come in to check it....
<!-- more -->
- NERF训练指令：

```
DATA_DIR=/cluster/home/lizeyu/multinerf/rawnerf/scenes/candlefiat
CUDA_VISIBLE_DEVICES=0 python -m train   --gin_configs=configs/llff_raw.gin   --gin_bindings="Config.data_dir = '${DATA_DIR}'"   --gin_bindings="Config.checkpoint_dir = '${DATA_DIR}/checkpoints'"   --logtostderr
```

服务器使用说明: [how to use server](https://sjtu-icat.github.io/post/21-01-01-server-usage/)
