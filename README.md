<h1 align="center">Dynamic Focus-aware Positional Queries for Semantic Segmentation</h1>

**This is the official repository for our paper:** [Dynamic Focus-aware Positional Queries for Semantic Segmentation](https://arxiv.org/abs/2204.01244) by [Haoyu He](https://charles-haoyuhe.github.io/), [Jianfei Cai](https://jianfei-cai.github.io/), [Zizheng Pan](https://zizhengpan.github.io/), [Jing liu](https://sites.google.com/view/jing-liu/%E9%A6%96%E9%A1%B5), [Jing Zhang](https://scholar.google.com/citations?user=9jH5v74AAAAJ&hl=en), [Dacheng Tao](https://www.sydney.edu.au/engineering/about/our-people/academic-staff/dacheng-tao.html) and [Bohan Zhuang](https://bohanzhuang.github.io/). 

***

><h3><strong><i>🚀 News</i></strong></h3>
>
>[2022-06-07]: Release code.

***

### Introduction:

We have proposed a simple yet effective query design for semantic segmentation under DETR-like frameworks, that the **positional queries are aggregated from previous cross-attention scores and the localization infromation** of the preceding layer.

![main](pics/main.jpg)

------

### Experimental results:

We provide single-seed experimental results and pre-trained models for FASeg:

| ADE20k val               | Backbone | Crop size | mIoU s.s. (%) | mIoU m.s. (%) | Params. (M) | FLOPs | Model |
| ------------------------ | -------- | --------- | ------------- | ------------- | ----------- | ----- | ----- |
| FASeg w/ conditional K_p | R50      | 512x512   | 48.3          | 49.3          | 51          | 72G   |       |
| FASeg w/ conditional K_p | Swin-T   | 512x512   | 49.6          | 51.3          | 54          | 75G   |       |
| FASeg w/ conditional K_p | Swin-L   | 640x640   | 56.3          | 57.7          | 228         | 405G  |       |

| Cityscapes val           | Backbone | Crop size | mIoU s.s. (%) | mIoU m.s. (%) | Params. (M) | FLOPs | Model |
| ------------------------ | -------- | --------- | ------------- | ------------- | ----------- | ----- | ----- |
| FASeg w/ conditional K_p | R50      | 512x512   | 48.3          | 49.3          | 51          | 72G   |       |
| FASeg w/ conditional K_p | Swin-T   | 512x512   | 49.6          | 51.3          | 54          | 75G   |       |
| FASeg w/ conditional K_p | Swin-L   | 640x640   | 56.3          | 57.7          | 228         | 405G  |       |

| Cityscapes val           | Backbone | Crop size | mIoU s.s. (%) | Params. (M) | FLOPs | Model |
| ------------------------ | -------- | --------- | ------------- | ----------- | ----- | ----- |
| FASeg w/ conditional K_p | R50      | 1024x2048 | 80.5          | 67M         | 533G  |       |

Considering the large variance on ADE20k and Cityscapes dataset, we will also report the multi-seed experimental results for FASeg later. The model will be uploaded in a day or two :)

------

### Installation

See [installation instructions](https://github.com/facebookresearch/Mask2Former/blob/main/INSTALL.md) for mask2former.

------

### Get started:

We provide training scripts for deriving all of our models:

```
# Train FASeg with R50 backbone and 8 GPUs on ADE20k:
python train_net.py --num-gpus 8 \
  --config-file configs/ade20k/semantic-segmentation/faseg_r50.yaml
  
# Train FASeg with Swin-T backbone and 8 GPUs on ADE20k:  
python train_net.py --num-gpus 8 \
  --config-file configs/ade20k/semantic-segmentation/swin/faseg_swin_tiny.yaml
  
# Train FASeg with Swin-L backbone and 8 GPUs on ADE20k:  
python train_net.py --num-gpus 8 \
  --config-file configs/ade20k/semantic-segmentation/swin/faseg_swin_large_IN21k_res640.yaml
  
# Train FASeg with R50 backbone and 8 GPUs on Cityscapes:  
python train_net.py --num-gpus 8 \
  --config-file configs/cityscapes/semantic-segmentation/faseg_r50.yaml
```

We also provide evaluation scrips for all of our models:

```
# Evaluate FASeg with R50 backbone and 1 GPU on ADE20k val:
python train_net.py --num-gpus 1 \
  --config-file configs/ade20k/semantic-segmentation/faseg_r50.yaml --eval-only MODEL.WEIGHTS "model/ade_faseg_r50.pth"
  
# Evaluate FASeg with Swin-T backbone and 1 GPUs on ADE20k val:  
python train_net.py --num-gpus 1 \
  --config-file configs/ade20k/semantic-segmentation/swin/faseg_swin_tiny.yaml --eval-only MODEL.WEIGHTS "model/ade_faseg_swin_ti.pth"
  
# Evaluate FASeg with Swin-L backbone and 1 GPUs on ADE20k val:  
python train_net.py --num-gpus 1 \
  --config-file configs/ade20k/semantic-segmentation/swin/faseg_swin_large_IN21k_res640.yaml --eval-only MODEL.WEIGHTS "model/ade_faseg_swin_l.pth"
  
# Evaluate FASeg with R50 backbone and 1 GPUs on Cityscapes val:  
python train_net.py --num-gpus 1 \
  --config-file configs/cityscapes/semantic-segmentation/faseg_r50.yaml --eval-only MODEL.WEIGHTS "model/ade_faseg_swin_l.pth"
```

For more usage, please see [Getting started with Mask2former](https://github.com/facebookresearch/Mask2Former/blob/main/GETTING_STARTED.md) and [Getting started with Detectron2](https://github.com/facebookresearch/detectron2/blob/main/GETTING_STARTED.md).

------

If you find this repository or our paper useful, please consider cite:

```
@article{he2022dynamic,
  title={Dynamic Focus-aware Positional Queries for Semantic Segmentation},
  author={He, Haoyu and Cai, Jianfei and Pan, Zizheng and Liu, Jing and Zhang, Jing and Tao, Dacheng and Zhuang, Bohan},
  journal={arXiv preprint arXiv:2204.01244},
  year={2022}
}
```

------

### Acknowledgement

The code is largely based on [Mask2Former](https://github.com/facebookresearch/Mask2Former). We thank the authors for their open-sourced code.
