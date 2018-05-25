# Human Related Paper Record
# Under Construction!
# Table of Contents
- [Human Segmentation](#human-seg)
- [Human Parsing](#human-parse)

## Human Segmentation
### PortraitFCN★ 
**[Paper]** Automatic Portrait Segmentation for Image Stylization <Br>
**[Year]** Eurographics 2016 <Br>
**[Author]** [Xiaoyong Shen](http://xiaoyongshen.me/), [Aaron Hertzmann](http://www.dgp.utoronto.ca/~hertzman/), [Jiaya Jia](http://www.cse.cuhk.edu.hk/leojia/), [Sylvain Paris](http://people.csail.mit.edu/sparis/), [Brian Price](https://research.adobe.com/person/brian-price/), [Eli Shechtman](http://www.wisdom.weizmann.ac.il/~elishe/), Ian Sachs <Br>
**[Pages]**  http://xiaoyongshen.me/webpage_portrait/index.html <Br>
**[Description]** <Br>
1) 粗读, 较早的用CNN做全自动portrait segmentation的paper, backbone为FCN;
2) 首先检测facial feature points，将portrait从图像中crop出来，并得到当前图像与canonical pose的homography transform (T). T用于对齐当前图像与canonical pose, 计算normalized的位置特征, 和得到形状先验.
3) position特征和shape特征与crop出来的人像一起作为FCN的输入, 由FCN得到最后的分割结果


### BSN★
**[Paper]** Boundary-sensitive Network for Portrait Segmentation <Br>
**[Year]** arXiv 1712 <Br>
**[Author]** Xianzhi Du, Larry Davis <Br>
**[Pages]** <Br>
**[Description]** <Br>
1) 提升边界分割精度的paper，主要针对portrait segmentation，提出三个策略 
2) individual boundary-sensitive kernel: 先用Canny从真值图中得到边缘，再通过dilation得到边缘的soft label。Kernel为1x3的vector，里面分别是从soft label计算得到的前景，背景和边缘的可能性。计算loss时用此Kernel为每个像素的不同channel加权
3) global boundary-sensitive kernel: 在训练集上通过统计平均的方法得到position sensitive prior。计算loss时用此Kernel对不同位置的pixel加权
4) boundary-sensitive attribute classifier: 没看懂

## Human Parsing
### Co-CNN★ 
**[Paper]** Human Parsing with Contextualized Convolutional Neural Network <Br>
**[Year]** ICCV 2015 Oral <Br>
**[Author]** [Xiaodan Liang](http://www.cs.cmu.edu/~xiaodan1/),  Chunyan Xu, [Xiaohui Shen](http://users.eecs.northwestern.edu/~xsh835/), [Jianchao Yang](http://www.ifp.illinois.edu/~jyang29/), [Liu Si](http://liusi-group.com/), Jinhui Tang, Liang Lin, [Shuicheng Yan](http://www.lv-nus.org/) <Br>
**[Pages]**  http://hcp.sysu.edu.cn/?p=666 <Br>
**[Description]** <Br>
1) 
