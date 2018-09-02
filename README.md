# Human Related Paper Record
# Under Construction!
# Table of Contents
- [Human Segmentation](#human-segmentation)
- [Human Parsing](#human-parsing)
- [Human Pose Estimation](#human-pose-estimation)
- [Datasets](#datasets)
- [Sources-Lists](#sources-lists)
# Rank
- Human Segmentation <Br>
  - ★★★ <Br>
  - ★★ <Br>
  **[Pose2Seg]** <Br>
  - ★ <Br>
  **[PortraitFCN]**, **[BSN]** <Br>
- Human Parsing <Br>
  - ★★★ <Br>
  - ★★ <Br>
  **[PGN]** <Br>
  - ★ <Br>
  **[High-Level Guidance]**, **[Co-CNN]**, **[PFCN]**, **[WSHP]**, **[Cross-domain Adversarial]**  <Br>
 - Human Pose Estimation <Br>
  - ★★★ <Br>
  - ★★ <Br>
  - ★ <Br>
 
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
**[Author]** [Xiaodan Liang](http://www.cs.cmu.edu/~xiaodan1/),  Chunyan Xu, [Xiaohui Shen](http://users.eecs.northwestern.edu/~xsh835/), [Jianchao Yang](http://www.ifp.illinois.edu/~jyang29/), [Liu Si](http://liusi-group.com/), Jinhui Tang, [Liang Lin](http://www.linliang.net/), [Shuicheng Yan](http://www.lv-nus.org/) <Br>
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

### WSHP ★ 
**[Paper]** Weakly and Semi Supervised Human Body Part Parsing via Pose-Guided Knowledge Transfer <Br>
**[Year]** CVPR 2018 spotlight <Br>
**[Author]** [Hao-Shu FANG](https://fang-haoshu.github.io/), [Guansong Lu](http://apex.sjtu.edu.cn/members/gslu@apexlab.org), [Xiaolin Fang](https://fang-xiaolin.github.io/), [Jianwen Xie](http://www.stat.ucla.edu/~jxie/), [Yu-Wing Tai](https://scholar.google.com/citations?user=nFhLmFkAAAAJ&hl=en）, [Cewu Lu](http://mvig.sjtu.edu.cn/)<Br>
**[Pages]** https://github.com/MVIG-SJTU/WSHP <Br>
**[Description]** <Br>
1) 粗读, 利用人体keypoint生成human parsing mask的一篇论文. 本文显示利用keypoint可以得到等好的人体解析结果. <Br>
2) 分为寻找相似pose, 生成part-level pior和image-guided refinement三步. 第一步, 利用keypoint找到与输入图像最相似的若干图像组成cluster; 第二步, 根据输入图像与cluster的关键的计算出仿射变换矩阵, 将cluster的part segmentation mask变换到与输入图像更相似的空间, 对所有cluster的变换结果取平均, 即得到piror; 第三步, 将输入图像叠加到第二步得到的part segmentation的heatmap上, 用一类似UNet的网络进行refine. <Br>

### ***Cross-domain Adversarial★***
**[Paper]**  Cross-domain Human Parsing via Adversarial Feature and Label Adaptation  <Br>
**[Year]** AAAI 2018 <Br>
**[Authors]** [Liu Si](http://liusi-group.com/), Yao Sun, [Defa Zhu](https://github.com/mathfinder), Guanghui Ren, Yu Chen, [Jiashi Feng](https://sites.google.com/site/jshfeng/), Jizhong Han<Br>
**[Pages]** https://github.com/mathfinder/Cross-domain-Human-Parsing-via-Adversarial-Feature-and-Label-Adaptation<Br>
**[Description]**<Br>
1) 提出了一个在标准数据集上训练, 在任意场景测试的cross domain人体解析算法. <Br>
2) 通过feature compensation network和feature adversarial network使在训练时source domain图像的特征接近target domain; 通过structure adversarial network使target domain最后输出的label具有接近一般人体的结构; inference时无需cross-domain model. <Br>
3) 问题: 1. 从实验结果看, feature adaptation和label adaptation的有效性并不能得到很好的证明; 2. label adaptation似乎与cross-domain之间没什么必然的联系, 况且真实图像中人的姿态并不都是单一直立姿态的. <Br>

### **PGN ★★**
**[Paper]**  MaskLab: Instance Segmentation by Refining Object Detection with Semantic and Direction Features  <Br>
**[Year]** ECCV 2018 Oral <Br>
**[Authors]** [Ke Gong](https://github.com/Engineering-Course), [Xiaodan Liang](http://www.cs.cmu.edu/afs/cs/user/xiaodan1/www/), [Yicheng Li](https://github.com/yicheng-li), [Yimin Chen](https://scholar.google.com/citations?user=rpLGwAQAAAAJ&hl=en), [Ming Yang](https://github.com/ufoym), [Liang Lin](http://www.linliang.net/)<Br>
**[Pages]** https://github.com/Engineering-Course/CIHP_PGN<Br>
**[Description]**<Br>
1) 分割+边缘检测做instance segmentation的一篇paper, 主要用于多人解析中. <Br>
2) 分为backbone网络, segmentation branch, edge detection branch和refinement branch四部分. backbone为resnet101, 把最后三个block concat起来作为多尺度feature送入接下来的branch中; segmentation branch和edge detection branch结构钢相似, 都使用了pyramid pooling, 此外边缘检测部分还使用了deep supervision, 即将最后三个block的feature拉出来做ASPP后都去预测边缘; 最后, 分割和边缘检测的结构concat起来送入refinement branch得到最后的分割和边缘检测结果. <Br>
3) instance partition部分, 首先水平和垂直地扫描, 根据edge确定属于同一instance的segments, 这些线段组成一连通图; 用BFS找到属于同一instance的pixel; 最后进行grouping, 去掉边缘检测的一些假边缘产生的小区域. <Br>
4) 提出了CHIP多人解析数据集, 这个数据集标注的比较精细. <Br>


# Human Pose Estimation


# Datasets
## Human parsing
[LIP](http://sysu-hcp.net/lip/): single-person parsing<Br>
[CHIP](http://www.sysu-hcp.net/lip/): multiple-person instance segmentation & parsing<Br>
[MHP](https://lv-mhp.github.io/): multiple-person instance segmentation & parsing <Br>
[PIC](http://picdataset.com/challenge/index/): relation-seg, muptiple-person segmentation <Br>
  
## Human pose estimation
[LSP](http://sam.johnson.io/research/lsp.html)
[FLIC](http://bensapp.github.io/flic-dataset.html)
[MPII](http://human-pose.mpi-inf.mpg.de/)
[MSCOCO](http://cocodataset.org/)
[AI Challenger](https://challenger.ai/dataset/keypoint)
[PoseTrack](https://posetrack.net/)


# Sources-Lists<Br>
https://blog.csdn.net/qq_36165459/article/details/78320535?locationNum=10&fps=1 <Br>
https://zhuanlan.zhihu.com/p/37933909 <Br>
