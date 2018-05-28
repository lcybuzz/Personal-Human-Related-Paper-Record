# Human Related Paper Record
# Under Construction!
# Table of Contents
- [Human Segmentation](#human-segmentation)
- [Human Parsing](#human-parsing)

# Human Segmentation
### PortraitFCN★ 
**[Paper]** Automatic Portrait Segmentation for Image Stylization <Br>
**[Year]** Eurographics 2016 <Br>
**[Author]** [Xiaoyong Shen](http://xiaoyongshen.me/), [Aaron Hertzmann](http://www.dgp.utoronto.ca/~hertzman/), [Jiaya Jia](http://www.cse.cuhk.edu.hk/leojia/), [Sylvain Paris](http://people.csail.mit.edu/sparis/), [Brian Price](https://research.adobe.com/person/brian-price/), [Eli Shechtman](http://www.wisdom.weizmann.ac.il/~elishe/), Ian Sachs <Br>
**[Pages]**  http://xiaoyongshen.me/webpage_portrait/index.html <Br>
**[Description]** <Br>
1) 粗读, 较早的用CNN做全自动portrait segmentation的paper, backbone为FCN; <Br>
2) 首先检测facial feature points，将portrait从图像中crop出来，并得到当前图像与canonical pose的homography transform (T). T用于对齐当前图像与canonical pose, 计算normalized的位置特征, 和得到形状先验.<Br>
3) position特征和shape特征与crop出来的人像一起作为FCN的输入, 由FCN得到最后的分割结果 <Br>

### BSN★
**[Paper]** Boundary-sensitive Network for Portrait Segmentation <Br>
**[Year]** arXiv 1712 <Br>
**[Author]** Xianzhi Du, Larry Davis <Br>
**[Pages]** <Br>
**[Description]** <Br>
1) 提升边界分割精度的paper，主要针对portrait segmentation，提出三个策略  <Br>
2) individual boundary-sensitive kernel: 先用Canny从真值图中得到边缘，再通过dilation得到边缘的soft label。Kernel为1x3的vector，里面分别是从soft label计算得到的前景，背景和边缘的可能性。计算loss时用此Kernel为每个像素的不同channel加权 <Br>
3) global boundary-sensitive kernel: 在训练集上通过统计平均的方法得到position sensitive prior。计算loss时用此Kernel对不同位置的pixel加权 <Br>
4) boundary-sensitive attribute classifier: 没看懂 <Br>

# Human Parsing

### *Deep Learning for Semantic Part Segmentation with High-Level Guidance* ★
**[Paper]** Deep Learning for Semantic Part Segmentation with High-Level Guidance <Br>
**[Year]** ICLR 2016 <Br>
**[Author]** [Stavros Tsogkas](http://tsogkas.github.io/),[Iasonas Kokkinos](http://www0.cs.ucl.ac.uk/staff/I.Kokkinos/), [George Papandreou](http://ttic.uchicago.edu/~gpapan/), [Andrea Vedaldi](http://www.robots.ox.ac.uk/~vedaldi/) <Br>
**[Pages]** <Br>
**[Description]** <Br>
1) 不太懂, 涉及到RBM <Br>
  
### Co-CNN★ 
**[Paper]** Human Parsing with Contextualized Convolutional Neural Network <Br>
**[Year]** ICCV 2015 Oral <Br>
**[Author]** [Xiaodan Liang](http://www.cs.cmu.edu/~xiaodan1/),  Chunyan Xu, [Xiaohui Shen](http://users.eecs.northwestern.edu/~xsh835/), [Jianchao Yang](http://www.ifp.illinois.edu/~jyang29/), [Liu Si](http://liusi-group.com/), Jinhui Tang, Liang Lin, [Shuicheng Yan](http://www.lv-nus.org/) <Br>
**[Pages]**  http://hcp.sysu.edu.cn/?p=666 <Br>
**[Description]** <Br>
  1) 采用类似U-Net的encoder-decoder结构, decoder阶段结合原图和encoder阶段的信息. <Br>
  2) 在最小的feature map后接一多类分类分支. 分类一支的loss参与全局梯度更新, 另外每个类别的概率与decoder中的每层feature map concat起来, 作为global image-level context <Br>
  3) 最后使用基于超像素的within-super-pixel smoothing和cross-super-pixel neighborhood voting <Br>
  

