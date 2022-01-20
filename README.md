# 标题：飞桨常规赛：中文场景文字识别 - 12月第3名方案

![GitHub forks](https://img.shields.io/github/forks/GT-ZhangAcer/PythonRepository-Template?style=for-the-badge) ![GitHub Repo stars](https://img.shields.io/github/stars/GT-ZhangAcer/PythonRepository-Template?style=for-the-badge) 

本项目为常规赛：中文场景文字识别 2021年12月份第3名的技术方案分享项目。最终得分为84.22158。

本项目使用PaddleOCR-develop(静态图版本)，PaddleOCR主要由DB文本检测、检测框矫正和CRNN文本识别三部分组成，本次中文场景文本识别只需要使用第三阶段的文本识别器即可。采用CRNN文本识别模型作为baseline
![image](https://user-images.githubusercontent.com/95835850/150290636-172d246a-8dc2-4764-bc54-6f506ef6739d.png)
本项目AI Studio地址：https://aistudio.baidu.com/aistudio/projectdetail/3290922?contributionType=1
从中可以获得更加详细的介绍

## 提交时所使用的checkpoint
最终比赛提交的结果，checkpoints使用的是/home/aistudio/work/PaddleOCR/output/my_rec_ch/路径下的best_accuracy

## tip1：合理的数据增强有助于提升比赛分数

本次比赛中，使用数据增强的目的是用来防止过拟合，并且数据增强适用于dataset较小的时候。

我选择使用text_render进行数据增强。使用的操作主要包括明暗变换，文本边界调整，添加噪声，颜色调整，文本字体特效变换等等。

## tip2：参数调优

本次比赛结果的调优过程：设定了161轮迭代（从epoch0到epoch160），初始学习率为0.0001，fc_decay为0.00001，l2学习率衰减为0.00001

为了适当提升学习速度，使用了cosine_decay和warmup。其中step_each_epoch为1000，warmup_minibatch为2000，衰减总轮数为161

经测试以上参数设定可以达到较好的结果

## 总结
每一种模型的能力是有限度的，从参数调优、数据增强等角度去改善也是有一定限度的。想要推陈出新，更显著地提升分数，小伙伴们可以去尝试使用新的网络，并对网络模型做出进一步调整。
