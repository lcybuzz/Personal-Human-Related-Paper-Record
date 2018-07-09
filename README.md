# Human Related Paper Record
# Under Construction!
# Table of Contents
- [Human Segmentation](#human-segmentation)
- [Human Parsing](#human-parsing)
- [Datasets](#datasets)
# Rank
- Human Segmentation <Br>
  - ★★★ <Br>
  - ★★ <Br>
  - ★ <Br>
  **PortraitFCN**, **BSN**, **Pose2Seg**  <Br>
- Human Parsing <Br>
  - ★★★ <Br>
  - ★★ <Br>
  - ★ <Br>
  **High-Level Guidance**, **Co-CNN**, **PFCN**  <Br>
# Human Segmentation
### PortraitFCN ★ 
**[Paper]** Automatic Portrait Segmentation for Image Stylization <Br>
**[Year]** Eurographics 2016 <Br>
**[Author]** [Xiaoyong Shen](http://xiaoyongshen.me/), [Aaron Hertzmann](http://www.dgp.utoronto.ca/~hertzman/), [Jiaya Jia](http://www.cse.cuhk.edu.hk/leojia/), [Sylvain Paris](http://people.csail.mit.edu/sparis/), [Brian Price](https://research.adobe.com/person/brian-price/), [Eli Shechtman](http://www.wisdom.weizmann.ac.il/~elishe/), Ian Sachs <Br>
**[Pages]**  http://xiaoyongshen.me/webpage_portrait/index.html <Br>
**[Description]** <Br>
1) 粗读, 较早的用CNN做全自动portrait segmentation的paper, backbone为FCN; <Br>
2) 首先检测facial feature points，将portrait从图像中crop出来，并得到当前图像与canonical pose的homography transform (T). T用于对齐当前图像与canonical pose, 计算normalized的位置特征, 和得到形状先验.<Br>
3) position特征和shape特征与crop出来的人像一起作为FCN的输入, 由FCN得到最后的分割结果 <Br>

### BSN ★
**[Paper]** Boundary-sensitive Network for Portrait Segmentation <Br>
**[Year]** arXiv 1712 <Br>
**[Author]** Xianzhi Du, Larry Davis <Br>
**[Pages]** <Br>
**[Description]** <Br>
1) 提升边界分割精度的paper，主要针对portrait segmentation，提出三个策略  <Br>
2) individual boundary-sensitive kernel: 先用Canny从真值图中得到边缘，再通过dilation得到边缘的soft label。Kernel为1x3的vector，里面分别是从soft label计算得到的前景，背景和边缘的可能性。计算loss时用此Kernel为每个像素的不同channel加权 <Br>
3) global boundary-sensitive kernel: 在训练集上通过统计平均的方法得到position sensitive prior。计算loss时用此Kernel对不同位置的pixel加权 <Br>
4) boundary-sensitive attribute classifier: 没看懂 <Br>

### Pose2Seg ★★
**[Paper]** Pose2Seg: Human Instance Segmentation Without Detection <Br>
**[Year]** arXiv 1803 <Br>
**[Author]** [Ruilong Li](http://www.liruilong.cn/), Xin Dong, Zixi Cai, Dingcheng Yang, Haozhi Huang, Song-Hai Zhang, [Paul L. Rosin](http://users.cs.cf.ac.uk/Paul.Rosin/), Shi-Min Hu <Br>
**[Pages]** <Br>
**[Description]** <Br>
  1) 结合pose做human instance segmentation, 与mask r-cnn相比对overlap的目标效果更好. 包括人体keypoint检测, Affine Align, 对每个align后的人分割三部分. <Br>
  2) keypoint检测部分使用hourglass结构, 得到每个人的keypoint; <Br>
  3) Affine Align是将ROI通过仿射变换, 将其与预先定义的模板对齐, 变换矩阵是通过最小化误差得到的. Affine Align后, 人体可以变得更加接近正常的竖直状态, 这可以提高对复杂姿态的性能; <Br>
  4) 将keypoint的feature与ROI concat起来, 完成分割. 用keypoint指导分割. <Br>
  5) 不足：I.分割性能很大程度上依赖于keypoint, 但对于多人keypoint检测只用一hourglass网络, 效果有限; II. Affine Align只包括平移, 缩放, 旋转, 实际效果是只能把倾斜角度很大的人体一定程度上修正到正常角度. 而且加入了最优化投影矩阵这一步骤, 使流程变得更复杂 <Br>

# Human Parsing

### *Deep Learning for Semantic Part Segmentation with High-Level Guidance* ★
**[Paper]** Deep Learning for Semantic Part Segmentation with High-Level Guidance <Br>
**[Year]** ICLR 2016 <Br>
**[Author]** [Stavros Tsogkas](http://tsogkas.github.io/),[Iasonas Kokkinos](http://www0.cs.ucl.ac.uk/staff/I.Kokkinos/), [George Papandreou](http://ttic.uchicago.edu/~gpapan/), [Andrea Vedaldi](http://www.robots.ox.ac.uk/~vedaldi/) <Br>
**[Pages]** <Br>
**[Description]** <Br>
1) 不太懂, 涉及到RBM <Br>
  
### Co-CNN ★ 
**[Paper]** Human Parsing with Contextualized Convolutional Neural Network <Br>
**[Year]** ICCV 2015 Oral <Br>
**[Author]** [Xiaodan Liang](http://www.cs.cmu.edu/~xiaodan1/),  Chunyan Xu, [Xiaohui Shen](http://users.eecs.northwestern.edu/~xsh835/), [Jianchao Yang](http://www.ifp.illinois.edu/~jyang29/), [Liu Si](http://liusi-group.com/), Jinhui Tang, Liang Lin, [Shuicheng Yan](http://www.lv-nus.org/) <Br>
**[Pages]**  http://hcp.sysu.edu.cn/?p=666 <Br>
**[Description]** <Br>
  1) 采用类似U-Net的encoder-decoder结构, decoder阶段结合原图和encoder阶段的信息. <Br>
  2) 在最小的feature map后接一多类分类分支. 分类一支的loss参与全局梯度更新, 另外每个类别的概率与decoder中的每层feature map concat起来, 作为global image-level context <Br>
  3) 最后使用基于超像素的within-super-pixel smoothing和cross-super-pixel neighborhood voting <Br>

### auto-zoom 
**[Paper]** Zoom better to see clearer: Human and object parsing with hierarchical auto-zoom net<Br>
**[Year]** ECCV 2016 <Br>
**[Author]** [Fangting Xia](https://sukixia.github.io), [Peng Wang](http://jerryking234.wixsite.com/pengwang), [Liang-Chieh Chen](http://www.stat.ucla.edu/~xianjie.chen/), [Alan L. Yuille](http://www.cs.jhu.edu/~ayuille/)<Br>
**[Pages]** https://sukixia.github.io/paper.html<Br>
**[Description]** <Br>

### PFCN ★ 
**[Paper]** Joint Multi-Person Pose Estimation and Semantic Part Segmentation <Br>
**[Year]** CVPR 2017 <Br>
**[Author]** [Fangting Xia](https://sukixia.github.io), [Peng Wang](http://jerryking234.wixsite.com/pengwang), [Xianjie Chen](http://www.stat.ucla.edu/~xianjie.chen/), [Alan L. Yuille](http://www.cs.jhu.edu/~ayuille/)<Br>
**[Pages]** <Br>
**[Description]** <Br>
1) 姿态预测和人体解析结合的一篇paper. 分为pose estimation和part segmentation两阶段. <Br>
2) pose estimation阶段, 先使用Pose FCN得到joint score map和joint neighbor prediction map. joint score map是h*w*14, joint neighbor prediction map是h*w*14*13*2(对每个关节得到其与其它关节点的位置偏置). 另外用Part FCN得到semantic part score map. 最后, 设计一Fully-Connected
CRF, unary term从joint score map得到, pairwise term由neighbor score map和semantic part score map设计特征得到. <Br>
3) part segmentation阶段, 从final pose estimation得到joint label map和skeleton label map, 作为两个feature map叠加到第一阶段的semantic part score map上, 用一小型FCN得到分割结果. <Br>
4) 关于如何利用不同类别在空间和语义上的内在关系, 本篇paper很值得借鉴. <Br>

# Datasets
[LIP](http://sysu-hcp.net/lip/) <Br>
[MHP](https://lv-mhp.github.io/) <Br>


