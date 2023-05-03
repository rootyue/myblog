---
title: "Games101 - Lecture 02 Review of Linear Algebra"
tags:
- games101
date created: 2023-05-03 15:28
---

# 课前说明

## 关键词

向量、矩阵、点乘、叉乘、图形学、长度、三角形、投影、坐标系、夹角、乘法、代数、线性代数、直角坐标、光线追踪、平行四边形、数学定义、定义自然

## 宣布一些事情

[00:06](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=6)
咱们这就开始在这个课之前，我们先说一说有几个事情宣布一下。首先一个是每一节的课后，然后我们的这个这个课件会以这个 PDF 的形式放出来，然后我们这个录播也会放到这个 games 的网站上，然后这两者都可以在我们课程主页上找到，也就是通过我的这个主页，然后有一个课程主页，然后找到了之后这个课件和这个录音都可以看到录像。然后这就是大家应该能够看到的这么这么一个表格，就是每一节结束之后都会有这么两个链接。然后有同学反映到说这个课件PDF，这因为访问涉及到大家从国内访问国外网站，然后会比较慢，然后从 games 的网站上大家也可以看得到这个在百度网盘上面上传的这个课件，所以说应该都没有问题。然后嗯，这里大概就是这么一个方式。

![](res/Lecture_02_Review_of_Linear_AlgebraPT1M6.556S.webp)

[01:05](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=65)
然后另外大家可以看到，比如说这个今天 14 号，然后这个说向量有线性代数，那么在这个课之前，我们就会把这个阅读材料给这个放出来，大家就可以先看就是阅读材料，指的就是那本书虎书的 Tiger book，然后他的第几章。然后这个阅读材料不做强制要求，就是说这些阅读材料只是说明这个是书里面和咱们这个课上要讲的这个相似的内容，大家如果愿意的话可以提前去学习学习，然后课程之后也欢迎再去阅读。好，就是说这本书本身就不做要求，那么大概就是这么回事。然后另外一个呢？这个今天是国内时间，已经是2月 14 号了，情人节，然后祝大家情人节快乐，然后如果大家现在还单身，祝大家早日脱单，早日找到另自己的另一半。然后如果大家这个已经有了另一半的话，这个祝大家有情人终成眷属，然后长长久久。好，那这个就说到这里。另外对，还有一点涉及到这个打赏的这么一个事情，这个毫无必要，这个就是说首先这是一个本来就是这个公众平台公益的性质，然后这个要打赏，就这个显得多少有一点这个嗯，不合适，这个反正感谢大家，大家要是愿意支持我就多过来上这个课就可以了，完全没有必要来做这个打赏。

## 上节课的内容

[02:25](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=145)
![](res/Lecture_02_Review_of_Linear_AlgebraPT2M56.788S.webp)

好，那就说到这里，那么这个我们上节课说到什么了？这个我们提到什么是计算机图形学？我们定义了一下，然后我们为什么要学习计算机图形学？然后我们提到了说我们这个课分为四部分，然后如果大家还记得的话，光栅化几何，然后这个光线追踪和这个模拟或动画这一块总共 4 块。然后课程涉及到这些网站，别的这些各种各样的这个这各方面的这些事情应该都已经交代到了。

## 这节课的内容

[02:56](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=176)
那么上一节课大概就说了这个事情，那么这节课咱们要就要从这个最基础的内容开始，一点一点把这个图形学的基础这个开始构建起来。那么图形学呢？其实依赖于很多东西，那咱们这节课主要是来说这个线性代数，大家可以看到这个标题非常恐怖，对不对？这个 Swift and Brutal introduction，然后这个其实是参考之前清华有门课的这个这个标题，那个我记得当时那门课叫计算机入门，然后这个课叫做 Swift and Brutal introduction to computer science，然后大家国内翻译成操快猛这个计算机入门，然后我们借用一下概念，然后其实怎么说大家现行代数这个概念其实本身并不难。然后大家看到待会咱们复习的时候，大家就会知道其实相对简单，没什么问题，咱们这节课只是说的快一些，然后这就是主要的内容。

[03:49](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=229)
那么咱们为什么要说线性代数？是因为图形学依赖于线性代数，其实图形学依赖于很多不同的东西，比如说这个基础的数学，像这个现行代数、微积分，然后统计，像这些都是这个非常用得到的一些知识。然后也涉及到一些基础的物理，主要就是涉及到光学和力学这些方面的知识。然后以及说随着现在图形学的发展，大家越来越看重说更高深一点物理学的知识。比如说其实我自己这边也在做类似的所谓波动光学的研究，就是说那当我们不能再假设这个光是直线传播这个时候，然后这种情况下，这个光作为一种光波如何与这个物体的表面材质进行作用，然后得到不同各种各样不同的这个外观，这都是这个图形学涉及到的东西。

[04:38](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=278)
光学和力学这里，然后这个还涉及到一些杂七杂八各种各样方面的知识都会涉及到。比如说这里我特别提到信号处理，因为有很多情况下我们要分析说这个出现了一些，比如说我们平常经常听到的一些走样这种现象，然后有一些叫做反走样技术，有很多这些技术在背后都是要解决一些信号处理的问题。然后另外数值分析这是一个非常重要的事情。有很多情况下图形学其实就是在解一些复杂的一些这个数学计算，比如说积分，像这个渲染整个过程其实就在解一个这个递归定义的积分，然后像这个模拟或者仿真，这里其实有很多在解一些比如说有限原因问题，或者说各方面的这些扩散方程之类的事情，就是说嗯，这块依赖的很多。然后图形学还要依赖于另外一点点，这一点给大家提一下，还需要一点点美学做出来一点东西之后，其实这个大家都希望这个图形，这个大家做出来的图形能够挺好看的，所以说有一点这个美感是很有必要的一件事情。

[05:37](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=337)
当然了上这门课也能够培养那么一点点，大概就是说我们会提到这么一些这个这些内容，这些渐渐的都会穿插在这门课里面，然后这个之后再给大家慢慢介绍。那么咱们这节课就会把这个线性代数说一下。嗯，包括这门课本身是一个入门的这个课，然后它更多的依赖一些基础的这些课程，特别是线性代数，然后线性代数我们主要说一些这个向量矩阵这些操作，对吧？向量涉及到什么点？乘，叉乘，向量这个矩阵涉及到矩阵和矩阵的乘，矩阵和向量的乘，然后比如说在图形学里面咱们要表示一个嗯，什么呢？一个点，对吧？x、y、 z 三个这个坐标，然后这个空间中的一个点，那我们用三个数来表示，这个实际上就是一种向量表示，然后这个涉及到各种各样的，比如平移、旋转、缩放，各种各样的这个操作，我们都可以把它给表示成这个矩阵和向量的乘法，所以这些是非常有必要的。

[06:37](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=397)
然而这些东西并不难，那咱们这个课，这今天这个课咱们就给大家这个复习一下，这里先给大家看一个这个例子，这个动画是我自己做的，然后这个，嗯，它为了说明的就是其实这个物体在旋转下它会看着是长什么样？这个蜗牛的这个壳，然后大家可以看到很多不同的这些发光点，然后但是这里大家要关注的点在哪？在这个蜗牛它本身是在这个不断旋转的，然后如果大家这个仔细看的话，其实这个蜗牛的旋转速度它一直在变化，也就是说它这个是从一边旋转到另一边，它会先加速到了中间旋转的最快，然后到了两边突然就停下，然后再回到这边也是一样，并不是以一个固定的速度来进行旋转。所以说包括这个旋转，这是一个非常简单的例子。

[07:27](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=447)
这然后这里就已经包括了不少这个背后的这些数学知识，所以说这个是很有意思的一个事情，然后这当然了，这就是一个旋转的例子，很简单，就是用一个旋转矩阵，然后咱们很快就会说，那么咱们今天的课最基础的内容咱们自然要从向量说起。好，然后这个向量这个概念叫做vector，然后涉及到数学和物理上面不同的定义，数学上更愿意管它叫向量，物理上更愿意管它叫矢量，就是那个箭矢的矢，就是射箭的箭，就是那个矢量。然后这个我们就管它叫向量好吗？这个没有什么关系，那么这个向量这从名字就可以体现得出来，它表示的是一个方向，那么嗯，在这里大家可以看到，比如说我有一个箭头，这个从 a 指向b，那么这个向量其实表示的就是从 a 指向 b 这么一个方向，那这个方向经常是怎么得来的？就是从这个 b 的坐标减去 a 的坐标，然后就可以得到这么一个向量，从 a 指向b，然后向量。如果你去平移这个向量，它表示的都是同一个向量，因为它只要指向同一个方向，那它就是同一个向量。

[08:38](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=518)
然后像这里这个 a b 向量， b 减a，然后这个嗯 b 减a，得到这么一个 a b 这个向量，然后我们也可以把它写作另外一个，用某一个字母来表示，比如说写作a，然后上面打一个箭头，然后或者这个印刷上面经常会涉及到这个向量，把它写作一个粗体的一个字母，然后写作 a 没有问题。然后这个向量最重要的有两个属性，一个是方向，就是这个 a 和b，它当然了向量表示的就是不同的方向，然后另外一个向量本身还能表示它的长度，所以从 a 到b，如果这个 b 离得远一点， a 和 b 之间这个距离长，那就是这个向量的长度要长。如果要短的话，向量短就相对较短。所以向量表示两个不同的内容，一个是这个方向，一个是长度。然后我们刚才提到这个向量，如果你平移它移动各个这个到不同的位置，那它表示的仍然是同一个向量，因为 a 和 b 之间的相对位置没有改变，所以说这个向量我们并不关心它的这个绝对的开始的位置，然后就是这么一个意思，然后向量我们刚才既然提到它的方向和长度，那我们就把它的长度可以直接写出来。

[09:49](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=589)
是什么呢？就是说比如说一个 a 向量，就是 a 上面的一个箭头，然后这个左边右边各加两个斜杠，然后这个表示的就是这个向量的长度，然后向量的长度这个有什么用？就是这个向量的长度可以给我们提供一个这个什么呢？给我们提供一种向量，叫做单位向量。什么叫单位向量？就是如果这些向量它表示的长度是1，那么这个就是单位向量。那么给你任何一个向量，你怎么把这个向量给变成单位向量呢？很简单，你去把这个向量本身去除，以它的长度，那么你得到的就是一个和你原始的向量同方向，并且长度为 1 的向量，也就变成了一个单位向量。

[10:29](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=629)
这也就是大家看到这里这个公式，大家可以看到这个公式，它这个是这个原始的这个向量 a 除以它的长度，然后我们把它定义成a，然后上面写一个这个东西，这个我们正常英文会管它读作 a hat， hat 就是那个帽子。然后正常情况下我们用这个形式来表示单位向量，然后在图形学里面可能更多的是大家一提到方向，就认为我们用一个单位向量来表示方向，然后我们不关心它的长度，好吧？然后那就是说我们用单位向量是可以直表示一个方向，那这个就非常好用。

[11:08](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=668)
然后在图形学里有涉及到各种各样不同的方向，然后咱们再待会再给大家这个一一解释。然后向量有很多基本操作，然后基本操作挺简单的，比如说最简单的操作就叫做这个向量求和，那么向量求和很简单，你要给两个向量，比如说给你 a 和b，然后给你这么两个向量，然后你如何去算出 a 加 b 是什么？那么这里有两个不同的解释，一个叫做平行四边形法则，一个叫做三角形法则，那么平行四边形法则是什么意思？大家看左边这幅图，那咱们可以把这个 a 和b，既然我们刚才说这 a 和 b 都可以任意的这个移动不影响它们的值，然后 a 和 b 我们可以把它放在同一个起点上，然后放在同一个起点上，那就是大家看到的左边这张图的左下角，然后然后我们把这个 b 和 a 都这个平行的搬移一段距离，使得这个 a 和 b 和另外一个 a 和 b 围成一个平行四边形。

[12:05](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=725)
那么这个平行四边形的对角线，这条红线就是 a 加b，那这是一个平行四边形法则，然后这样可以告诉我们两个向量加起来是什么，然后另外向量还有一个计算方法叫做三角形法则，三角形法则在这个图形学里面用的也挺多，就是说这个很简单，我们要相加若干向量，我们就把这些向量首尾相接的拼起来，那么最后形成的这个最开始和最结束我们把它连起来。那就是这个相加的和，那这个不只适用于一两个向量，就很多向量也可以这么做。

[12:37](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=757)
比如咱们看右边这幅图，这个这要算 a 加 b 怎么办？把这个 a 和 b 首尾相加，也就是说把这个 b 的开始放在 a 的结束上，然后 a 加b，也就是从 a 的起点到 b 的终点，那如果 a 加 b 加c，大家可以这个一直这么操作下去，那这个就很方便。然后这两种不管是平行四边形法则还是这个三角形法则，最简单的做法就是，嗯，通过这么一种几何的这么一种理解，然后来看这个在几何上两个向量加起来是什么。那么还有一个理解，就是在这个数学上或者代数上，这个向量相加是什么呢？那就是直接把他们的这个坐标加起来，这个非常简单，这个很快就要跟大家说，大家如果看这个例子，就是说我们现在在描述同样是一个向量a，但是这里大家会看到这个有一个这个坐标系在这里面，然后有一个x，有个y， x 向右， y 向上。然后这个这里就其实是在用这个直角坐标系，或者叫笛卡尔坐标系来描述这个向量。

[13:43](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=823)
那么这个向量什么意思？我就认为这个向量永远都是从这个圆点开始，零零，也就是左下角，然后这个沿着 x 有一些这个单位向量，然后向右走这个大家可以看到这个 x 被分成了好多段，这就认为是这有很多不同的职业单位。然后 y 方向也是一样，这个分为好多段，那么一个向量到底是多少，我们就可以用几个 x 加几个 y 来表示，然后通常这个 x y 是这个定义成这个互相垂直的，并且都是单位向量。然后这个像这里的情况，这个 a 向量黄颜色表示，我们就可以把它表示成 4 个 x 加 3 个y，大家可以看到这个比较清楚，对吧？然后这样的话有什么好处？就是说我们可以直接用这个坐标 4 和 3 这两个数来表示这么一个向量，那在这里这个 a 向量，大家可以看到左下方这个 a 向量写作 x y，这个 x y 就是表示它这个前面的数就是多少个 x 和多少个 y 的意思，那么这就是它的这个坐标表示。

[14:42](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=882)
然后这里有一点在图形学上，我不知道在其他的领域怎么样定义。在图形学上大家默认给一个向量，如果不说它是一个什么样的形式，我们就认为这个向量是一个这个往下写，也就是说任何一个向量，这个缺省的设置是这个向量是个列向量，就是一列数。好，然后这个向量我们也可以把它给变成一个这个横的，也就是变成一个行向量。

[15:09](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=909)
像这个中间大家看到的一个 a t 等于 x y，这个 t 是什么意思？就表示这个转置就是把这个任何一个向量的行和列互换，那自然是这个原本是默认是列向量，那么这个转置之后就变成了这个横向的 x 和y，横着写这个在矩阵上面大家也会这么用。然后我们为什么要这么写这个定义这么一个i，这个 x 和 y 这个直角坐标，是因为如果我们这么定义的话，对于两个轴如果垂直，而且又是这个以单位向量这么一节一节给加起来，就是说那我们算这个向量长度就非常简单，那怎么算呢？比如说像这里这个二维的向量，对吧？然后我们就用它的x，嗯，平方加上 y 平方，然后开个根号就可以得到这个向量的长度。然后比如说像这个情况，大家看到水平方向是四个格子，竖直方向是三个格子，那么这个大家知道这个勾股定理，就告诉大家这个向量的长度是5，那也就是说我们把向量表示成直角坐标系的这样一种代数形式，是非常有助于计算它的长度的。所以这就是为什么大家平常会用一套坐标系，那大概就是这么一个道理，那向量呢？加法以及他们这个之前的这个表示都是非常简单的。

[16:25](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=985)
那么向量更广泛的用法，也就是这节课主要跟大家说的两个这个计算，就是向量的这个点乘和差乘这么两个计算，那么都是什么意思？这个就是说这个，嗯，向量的乘法，它和这个数的乘法不太一样，像我们提到数的乘法，那就是乘法，那向量的乘法其实两个不同类型的乘法，那也就是说两种不同的运算。

[16:51](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=1011)
那咱们把这两个分别看明白好吗？就是说，比如说啊，大家现在看到这个屏幕中间这有两个向量， a 和b，然后这个向量的点乘是什么意思？就是这么定义的，大家可以看到这个 a 向量点乘 b 向量，然后等于这个等于什么呢？等于 a 的长度乘以 b 的长度，再乘以它们两个之间夹角的余弦，然后就是这么这么一个定义，然后这个定义自然是最标准的定义了。

[17:22](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=1042)
比如说给大家给定了两个不同的向量，那么它长度我们自然知道，然后这个两个向量之间的夹角，我们假设能够算出来，然后这个用一个余弦 cosine 就可以算出来这个数是多少。那么有一点这个是需要这跟大家说明的，就是说这个大家看到从这个 a 向量点乘，这个 b 向量中间打个点，这个最后的结果你看 a 向量的长度是一个数， b 向量的长度是一个数，这个余弦仍然是一个数，所以说这三个数乘起来它其实还是一个数。所以左边是两个向量，然后它的点乘是一个数字，然后或者叫做一个数量，然后就是说这里就是点乘能够告诉大家的结果就是说向量的点乘给大家，最后得到的是一个数。那么下面要给大家说的就是说，嗯，这个定义我们要怎么用它？特别是在图形学里怎么用它？这个很简单，比如说我们可以做一个简单的变换，把这个 a 和 b 的长度拿和那个 a 和 b 的点乘拿到一边去，把这个夹角的余弦放在另一边，那也就是发现大家可以看到这个左下角的这么一个画面。

[18:29](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=1109)
一个定义这个给定两个向量，两个向量之间夹角的余弦是他们的点乘，然后这个除以他们这个各自的长度的积，那么也就是说给你两个向量，大家立刻就可以算出这个，嗯，这两个向量之间的夹角余弦也进而可以算出两个向量之间的夹角。也就是说点乘可以帮助大家快速的得到这个两个向量之间的夹角，特别是在一个什么样的情况下最方便？特别是在两个向量都只是方向，也就是都是单位向量的时候，大家可以看右边这个公式，当两个向量都是单位向量的时候，它们的长度自然都是1，所以它们的点乘自然直接就是它们夹角的余弦，所以这个时候只需要我们做一个这个反余弦，我们就可以得到这个这个两个向量之间的夹角，所以向量的点点乘是很有用的。

[19:24](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=1164)
那么说到现在其实还没有说明这个向量点乘要怎么算，对不对？然后这个我们之后在代数的这一方面，然后给大家解释。那么这个点乘，然后它本身既然是一种运算法则，都会满足各种各样不同的这个性质，比如说点乘满足这么几个性质，这个和数字的乘法非常相似，什么呢？交换率、结合率和分配率，对吧？这个大家可以看到，交换率，也就是说 a 和 b 点乘，等于 b 和 a 点乘，这个挺好的。然后如果 a 和 b 加 c 这个做点乘，那么就等于是 a 和 b 做点乘，然后再加上 a 和 c 做点乘，然后如果有一个数字 k 去乘以某个向量，再和另外一个向量做点乘，那就好像是说这个某个向量和这个 k 应用在另外一个向量上，他们两个做点乘，或者说先做点乘，在前面再乘以一个k，这个问题都不大。

[20:20](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=1220)
这些是这个向量的一些基本属性，这个向量点乘的一些基本属性，然后我们刚才就提到这个事情，就是说这个点乘自然有它的定义，对吗？就是 a 的长度， b 的长度，然后夹角的余弦乘起来，那么在这个直角坐标系或者笛卡尔坐标系下，他们其实这个点乘的运算会更加简单，为什么呢？因为大家可以看到，比如说在二维的情况下，我们用两个数 x y 来表示一个向量，那 a 就是 x a，然后 y a，然后这个 b 就是 x b y b，然后他们两个的点乘就是 x a 乘 x b 加上 y a 乘 y b，大家发现这个就是其实就是对应的元素相乘并且加起来。

[21:04](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=1264)
那么这个道理可以同样扩展到高维，在三维上也是一样的，就是说这个两个向量在三维上，那自然怎么表示呢？那就是用x，a，y，a，z， a 这三个数，然后表示a，然后 x b、 y b， z b 这三个数表示b。那么这个两个向量怎么做？点乘很简单，也是对应元素点乘，x，a，x， b 加上y，a， y b 加上 z a， z b。就是说对应的元素相乘，再把它们加起来。那么从这个过程大家可以清晰的看到这个给定的两个数，两个这个输入都是向量，都是这个 3 个一组或者两个一组，对吧？然后最后的结果就是一个数，这也就是点乘的性质，那么就是通过这种方法来计算的，然后这个点成，我们刚才已经提到它最大的作用，特别是在图形学里面，就是用来找到这个两个向量或者两个方向之间的夹角，然后或者说是余弦夹角。

[22:00](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=1320)
然后呢？嗯，特别是比如说我们之后在做光照模型的时候，我们知道光从哪一个方向进来，然后这个物体表面的法线是什么样的，然后这个我们从哪个方向去看，那这些方向之间互相的夹角，这个计算都是通过点乘来这个运算的。然后这个点乘还有另外一个这个很有用的事情，就是说我们要找到这个一个向量投影到另一个向量上是长什么样，这个是什么意思？大家可以看这么一个例子，就是说我们现在看 a 和b，它们两个方向是不一样的，然后但是我现在希望把这个 b 向量所谓投影到这个 a 向量上去，那是什么意思？就是说假设有一束这个光线平行着的，然后他们垂直着 a 方向照过来，那么这个 b 自然会投出一个阴影在 a 上，那投出这个阴影这一段，我们就管它叫做这个 b 在 a 上的投影，然后这个大家就会看到这里是应该怎么计算它，这个这里就需要用到刚才我们提到的这个向量的这个基本属性的知识。

[23:09](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=1389)
那向量有哪两个属性？有方向和大小和长度，对吧？那么既然是 b 向量投影在 a 市 a 向量上，那么这个投影一定是沿着 a 方向，对吧？所以说首先这个投影，这个所谓 b purp，这里这个东西这个符号叫做purp，也就是 purp and dicular 的缩写。

[23:31](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=1411)
这个 b purp 的这个方向就已经定下来了，它一定是沿着a，对吧？因为我们要算它沿着 a 的投影，那么一定我可以把这个 b purp 表示成这个 a 向量对应的方向，也就是这个 a 的单位向量 a hat 乘以一个长度这个k，那么现在只要我们能够把它的长度算出来就可以了，对不对？那么怎么算它的长度呢？那大家看到这里这个有一个直角三角形关系，因为我们要把 b 向量投影成 b purp，那么这里自然有一个这个直角三角形在这里存在，也就是从这个嗯， b purple 的终点到这个 b 的终点，然后这么一条边，然后还有 b purple 本身加上这个 b 向量自己，那这个形成了一个直角三角形，那么 b Perp 的长度是多少呢？那也就是 b 的长度乘以这个 a 和 b 的夹角余弦，对吧？然后也就是这里为什么是 b 的长度乘以 cosine c 的，然后这个夹角鱼弦怎么做大家已经知道了，直接拿这个点成这个 a 和 b 的点击，然后它会告诉我们夹角的鱼线，所以这里就等于是能够把一个这个，能够把这么一个向量在另外一个向量的投影算出来，那么投影算出来有什么好处，对吧？然后这个，嗯，投影算出来有一个好处，就是说我们可以把一个向量分解成两个向量，其中让一个方向这个平行于某方向，然后另外一个方向垂直于某方向。

[25:01](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=1501)
比如说像这里我们既然知道 b purp 怎么算，那么另外一个方向这个 b 减去 b purp，我们就可以知道是什么。然后这里减法不给大家多做介绍，因为减法跟加法是互逆的，就是说这个，嗯， b purp 这一段加上这个 b 减去 b purp 这一段加起来之后，大家用平行四边形法则会发现，唉，这个就等于这个 b 向量没有问题。

[25:25](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=1525)
那么嗯，这个，嗯嗯，这就是点乘能够给大家带来的一个好处，就是说大家可以把一个向量任意的进行这个垂直与平行的分解，然后这是一个很重要的事情。那么在图形学里面这个点乘还会给大家这个另外的一些好处，比如说我们可以计算这个两个向量或者两个方向有多么接近，那什么叫接近呢？就是说我们可以算这个两个向量的这个点乘的结果，然后根据他们点乘的结果，我就知道它是否是接近还是远离这两个方向，那待会给大家说。然后这个向量的点乘还可以告诉大家关于一个前与后的信息，这个事情非常有用。

[26:07](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=1567)
那什么意思？咱们可以看一下这个例子，就是说大家可以看到如果这个有一个向量 a 给定了某一个方向，那么我可以这个考虑到这个，嗯，比如说从 a 的起点向这个整个上面方向看过去，以及向下面方向看过去，然后各会形成一个半圆。然后在这里整个大家可以看到一个整个圆被分成了两部分，一部分在这个上半部分，我们认为如果有一个向量是处于这一部分的，就是说它的终点是落在整个这个虚线以上的，那我们就认为这个 a 和 b 是属于基本上算是相同方向，或者说都是向前的。然后如果有一个向量，比如像这里向量c，它的终点落在了这个曲线的下部分，然后这个时候我们就认为说这个，噢， a 和 c 他们两个方向基本是相反的，那么这里怎么样判定这个事情？就是说这就是点成的一个好处，就是说我们如果用这个 a 和 b 向量求点乘，我们会发现这个点乘会给我们一个这个大于 0 的值，也就是正数。然后如果我们去点乘 a 和c，然后这里的点乘的结果会告诉我们这是负数。

[27:19](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=1639)
然后如果说有一个向量正好它的这个终点在这个虚线上，那么这个 a 和这个向量求了点乘之后，会给我们一个 0 这么一个结果，那就是说，嗯，这个向量的点乘可以告诉我们方向性，就是方向基本一致或者方向基本相反，或者方向垂直。那么同样道理，点乘也可以告诉我们这个这两个向量有多接近，比如说这个 b 向量和 a 向量它就比较接近，然后我们求点乘点击的时候，这个得到的结果就会比较接近1，然后如果说这个 b 向量渐渐这个方向和 a 远离了，比如说远离到一个什么程度到和 a 垂直，它就会渐渐变成0，然后这个再远就会渐渐变成-1，直到他们俩完全相反这个方向。

[28:06](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=1686)
然后他们两个如果都是方向量的话，那么点乘的结果会这个从这个 1 就是完全相同的方向变成完全相反的方向，也就是-1，就是说它这个值可以告诉大家这两个向量在方向上有多么接近。然后这个很有用的，就是说这个之后，这个大家会看到这个之后这个在图形学中的应用，然后这里就是点乘，那么嗯，这样哈，我们很快要给大家介绍这个叉乘。然后在这个之前我先看一下这几个大家之前有没有什么讨论的一些问题。我明白了，大家有同学问这个说为什么要用这个？为什么要用？为什么？为什么默认是个列向量，这个是约定俗成的一件事情，当然可以用这个航向量，有一些书是用航向量没有问题，但是就是说更多的应用，比如说特别是在这个图形学的这些硬件上面，这个或者说 API 上面这个 open GL 之类的东西，大家默认都是在用这个这个默认的列向量。然后这样的话所有的矩阵可以佐乘这个之后我们再给大家说，然后嗯，这个有人问有什么应用点成的这个说为什么两个向量是否接近？这个有什么应用？这里这个很简单，比如说这个大家看一个镜子，然后有一束光打在这个镜子上，然后大家知道有这个镜面反射这么一个反射的定律。

[29:30](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=1770)
那如果说你的眼睛这个是，就是这个啊，嗯，就是从它的这个镜面反射出射光的这个方向上看过去，那你就会看到一个反射的点非常亮，如果你这个眼睛稍微这个和这个方向错开一点点，那你就看不到这个反射。那如果对于金属来说，金属的这个高光是怎么来的？同样的道理，就是说入射的入射光打到这个金属表面，它会反射，然后在这个它的镜面反射的这个方向周围，然后如果你从那这些方向去观测，那这个得到的结果都是这个基本上属于在这个高光里面，那如果说离得远了你就看不到。所以我们需要有一个办法来这个提供这个两个向量是否接近这么一个标准。

[30:13](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=1813)
好吧？那大概就说到这，然后这里这个我们继续往后说这个向量的这个差级。那么向量的差级是什么意思？就是这是另外一种计算，它虽然也是乘法，但是它是和刚才的点击是完全不一样的计算。那么这个大家可以看到这是一个示意图，所谓这个叉机它会输入两个不同的向量 a 和b，然后它会给这个给出，也就是计算出另外一个向量，这个计算出的这个向量，也就是说这两个向量的原本这个输入向量的这个差积的结果和原本的两个向量都要垂直，那么大家想一想，那既然这么定义了的话，嗯，这个叉乘之后的向量假如说咱们把它记作c，那么 c 要垂直于 a C 又要垂直于b。

[31:02](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=1862)
那么 c 必然垂直于 a 和 b 所在的平面，那也就说明了这个向量 c 一定和 a 和 b 不在一个平面内，对吧？然后这个大家可以从这个公式的定义上面来看，就是说我们会写 AX 乘b，然后这个它的定义是这个 a 的长度乘以 b 的长度，再乘以 sin c 态其实还需要一个方向，这里这个这里写的并不并不正确，就是说不是说不正确，而是不完善，就是说这里只是给大家定义了 a 这个叉乘 b 的嗯，这么一个大小应该是多大？但是它的方向并没有写出来，然后它的方向应该如何决定？我们刚才说这个叉乘会给大家一个新的向量，垂直于 a 又垂直于b，这里就需要大家应用一个叫做右手定责的一个这个规律。

[31:51](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=1911)
什么叫右手定责？很简单，伸出右手来，说起来是这样，有两种不同的右手定责，一个是伸出你的这个右手的三个指，这个拇指、食指和中指，这样的话，然后你会把它给摆成一个这个互相垂直的一个方向，这是一种右手定则。但是在这里我们给大家介绍的是另外一种叫做右手螺旋定则，大概是这么一个意思，就是好像大家点赞这么一个样子，什么意思？就是说大家是这个 4 指的方向，代表了一种旋转的方向，就是说我们要算这个 a 和 b 的这个叉乘，或者说叉积，那我们就从 a 旋转到 b 方向，那么这个拇指对应的方向就是它这个向量的这个这个他们两个向量叉乘出来得到的这个结果，它的方向。

[32:37](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=1957)
那么这里大家可以对照这个屏幕，这个 a 和 b 大家看一下，对吧？从 a 绕到b，那自然就是向上的，那那么这个给大家这个既然说了这个右手定责哈，那咱们大家可以试一下，那如果 b 插成 a 是什么呢？那大家可以想象一下，从 b 插成a，抱歉，对大家做这个动作并不意味着什么事情。

[32:57](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=1977)
这个从 b 到 a 这个转过来，大家会发现这个 BX 乘 a 其实得到的一个向量正好和 AX 乘 b 相反，他们的这个上下这个方向是相反的。然后这也就告诉我们向量的差积并不满换率，如果我们要交换两个向量的差乘的顺序，那么必须得加上一个负号，就是这么个意思了。

[33:23](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=2003)
好，然后这个，嗯，向量的差积有什么作用？我们可以用它来建立一个三维空间中的直角坐标系，然后这里大家就可以看到这是什么意思。比如说这个在三维空间中大家给定了一个 x 轴和一个 y 轴，然后我们可以通过 x 轴叉乘 y 轴的方式算出 z 轴是什么，这个就是这个向量叉乘的这么一个其中一个明显的作用。那同样道理，大家可以这个试试看这个比如说用 y 轴叉乘 z 轴会得到x，对吧？然后 z 轴叉乘 x 轴可以得到y，这个大家只要这个对右手这个螺旋定则把握对了，就应用对的话，就是这些正负。这个左边列出来这 6 个是一定不会有问题的，咱们就只用记住头一个就 x 叉乘 y 得到z。

[34:11](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=2051)
另外这里多说一句，就是说如果说在一个三维的坐标系里面， x 和 y 的差乘得到的是z，那么我们就说这个坐标系是一个右手坐标系，因为大家是通过右手这个螺旋定则算出来的这个 z 方向。然后我们在这门课里面考虑的全部都是右手坐标系。然后大家如果说会接触到这个 open GL 或者是一些别的什么什么什么，嗯，这个 API 里面他们会假设说我们用的是左手坐标系，也就是说 XX 乘 y 得到的结果是负z，这个就非这个就不是很方便，特别是作为教学用途，我们觉得我们在这里就这个做一个这么一个这个假设，我们认为这个叉乘如果 x 叉乘 y 得到z，那这就是右手戏。

[35:00](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=2100)
然后咱们这个就一直用这个右手戏，好吧？然后我们看右侧这里面有几个不同的这个性质，我们刚才提到这个叉乘没有交换率，有交，如果要交换顺序一定要加一个负号。然后我们现在想另外一个事情，就是说这个一个向量叉乘，它自己得到的是什么呢？得到的是0，为什么呢？咱们刚才回到刚才这个叉乘的这长度，叉乘的长度是两个这个输入向量的长度，再乘以它的这个夹角的这个正弦值。我们知道这个两个向量如果它是重合的，那它们两个夹角是0，正弦就是0，所以这个得出来的结果是一个长度为 0 的向量。

[35:40](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=2140)
这里是需要跟大家指出的，就是说这个不管怎么样向量叉乘得到的都是另外一个向量，所以它是一个向量，但长度是0，所以它是个 0 向量，所以它并不是一个 0 这么一个数字，这个大家知道就好。然后后面两个都相对简单，这个分配率和结合率仍然存在。好，这里就是说这个向量的这个叉乘，然后向量的叉乘在这个代数上也是可以直接写出来的。然后大家可以看到这里叉乘这个相对较为复杂一些，但是没有关系，大家看这个上半部分就是 a 向量叉乘 b 向量，假设都是 x a y a z a 这种表示方法，那么得到的是一个向量，大家可以看到又是一个列向量，是这个三个元素，三个元素分别是这么算出来的，知道就行。

[36:25](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=2185)
也就是说通过这个在这个笛卡尔坐标系下向量的查乘，也可以非常明确的写出来，然后这里给大家这个多说一句，这个之后我们会在这个，我们会在这个后续的讲座里面再继续说，就是说这个向量的叉乘可以表示成矩阵形式，就是说我们可以把这个向量 a 写成一个对应的矩阵，然后我们再用这个矩阵去乘以这个向量b，然后一样可以得到这个上面写出来的这么一个结果。

[36:56](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=2216)
那么嗯，这里之后很快就会给大家讲，好吗？然后那咱们刚才提到这个向量的这个叉积或者叉乘这个怎么算，对吧？那么它到底有什么样的作用？特别是在图形学里面有什么样的作用？这个作用当然特别重要，那这里我列出两点，第一判定左和右，第二判定内与外，当然这两个是同一个概念，然后是什么意思？就比如说给你两个向量，然后你可以算出来它的这个差积是多少，那为什么就能告诉大家左和右的信息？那咱们看下面这么两个例子，那大家看左边这个这幅图，左边这幅图，假设大家现在在看一个平面，一个平面，然后这个平面是 x y 平面，也就是所有这个操作都是 x 跟y，这个 z 是大家可以通过这个右手螺旋定则，可以这么算出来， XX 乘 y 就从 x 绕到 y 那么大拇指对应的方向 z 算出来右手细没问题。

[37:54](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=2274)
那么这里如果大家有两个向量， a 和b，大家想判定这个 b 在 a 的左侧还是右侧，那什么叫左侧？右侧就是从 a 我这个向左旋转，或者说逆时针旋转，还是说向右旋转？顺时针旋转，就这么个意思，那现在这里大家可以看到，嗯，这个 b 向量应该是在 a 向量的左侧，没问题，我直接可以看得出来。

[38:17](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=2297)
那么在数字上如何表示？很简单，那么用 AX 乘 b 得到的结果，大家会发现这个 z 是正的，那就说明 b 在 a 的左侧，那如果说反过来，那 a 是不是在 b 的右侧？咱们可以试一试。比如说 b 插成a，那应该是这么一种方式啊， b 插成 a 这样一种右手螺旋的方式，然后大家会发现，噢，大家得到一个向量，这个向量的 z 必然是负的，那就说明这个 a 是在 b 的右侧，然后这个是没有问题的。所以说叉机可以告诉大家这个向量的左和右这么一个关系好。

[38:50](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=2330)
然后，嗯，那么我刚才还提到判断左和右是一方面，那么另外一方面就是判断内和外这一点在这个图形学里就得到相当广泛的应用了。比如说一个非常这个直接的例子，现在大家看到右侧有一个三角形a、b、c，然后有一个点 p 点，这个 p 点我想问他是不是在三角形内部？嗯，就是这么一个事情，那这个问题大家要如何回答？那这里就需要用到咱们的这个这个这个叉机的这么一个应用了。那么我们刚刚提到左和右这么一个信息，假设说咱们有这个a、b、 c 这么三个点，这三个点是逆时针排列的，那么咱们可以做这么一个，这是差级，谁和谁呢？先看 a b 和 a p，就是说这个点p，现在是大家看到在三角形里，然后这个 a b 叉乘 a p 得到的结果是向外的，对吧？然后也就是说这个 p 点是在 a b 的左侧，没问题，那咱们对于 b c 来说可以做相同的操作，用 b c 去插成 b p，我们就可以得到o，OK，没问题， p 点仍然在 b c 的左侧。

[40:03](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=2403)
然后呢，大家再看 c a，大家注意这个绕的顺序， a b c。所以应该是 a b b c c a。然后大家如果看这个 c a，那么这个 p 点也在 c a 的左边，诶，那，那这就说明什么呢？这就说明这个 p 点在三角形的内部，否则的话一定至少得有一边，使得这个 p 点它是在这个某一个这个边的右侧。我不信的话，大家可以把这个 p 点大家脑补一下。把这个 p 点放在这个 a C 这个右边，放在 a C 右边，大家会发现，OK，判断 a b 的时候，好，它仍然在 a b 的左边。没问题。判断 b c 的时候， b c 叉乘 b p 仍然可以得到这个结果，它在 b c 的左边，那么在判断 c a 和 c p 的时候就不是了，因为那个时候如果 p 点在外面的话，那就变成了这个 p 点在 CA 的右边。

[40:52](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=2452)
对，所以说通过这个叉乘，我们可以立刻的判断这个三角点是不是在三角形内。那么这个大家可能会问一个问题，这里你先假设了三角形这个a、b、c，它的这个绕向它本身这个规定，这三个点就是逆时针排布。那假如说我有个三角形，我比较倒霉，我写成了 a C、 b 这么一种形式，就是a、b、 c 的排布变成了顺时针，那这怎么办？这个没有问题，为什么呢？因为这个时候你会发现在这个时候这个 p 点都在三条边的右边，也就是说如果大家想判断的一个就是说最准确，最这个合理。

[41:32](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=2492)
对于任何的这个三角形，a、b、c，不管你的输入顺序是逆时针还是顺时针的，那我们都可以说这个都可以算对，那怎么判断呢？就判断这个 p 点一定一直在三条边的左边，或者是都在三条边的右边就对了，就是这样的话，就直接就可以这个忽略这个三角形给定的这个三角形三个点的顺序，那么这点非常之重要，这就是之后大家做这个三角形的这个光栅化的一个基础，我们要判断三角形覆盖了哪些像素，那我们自然要知道这个像素这个是不是在三角形内部，然后我们好给这个像素进行着色。

[42:11](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=2531)
对，那么有同学会问了，那如果得到结果正好是0，那怎么办？那算是在内部，算是在外部，就是说这个正常情况下，在图形学里面，咱们这个正常的考虑就是像这种，我们管它叫 corner case， corner case 意思就是说呢这种情况你自己决定，你说它在里面行没问题，说它在外面也可以。咱们之后做光线追踪也会涉及到这个问题，假如说有一个光线正好擦至三角形一个边过去了，你说这算相交不算这个这自己说了算，就是这么个意思。

[42:42](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=2562)
好，然后这个这就是我们这个关于这个向量叉乘的一个应用，然后向量叉乘之后我们还会再继续提到。好，那么这里既然定义了这个向量的这个基本操作，然后我们就可以说用这些向量来定义一些这个不同的这个坐标系，其实刚才咱们已经这个跟大家说了，对吧？然后这个就是说我们用这个向量的叉乘，我们可以定义一些互相垂直的轴，让这些轴就会形成一个坐标系，我们刚才提到右手系，对吧？然后我们如果定义这样一个这个坐标系，向这里定义u、v、w，然后u、v、 w 认为这 3 个向量都是单位向量，然后并且它们之间的这个都互相垂直，也就是点乘的结果都是0，然后给你 u 和v，你是叉乘得到w，对应就是 x y 叉乘得到z，这样的话得到的结果自然就是这个一个右手的这个直角坐标系，然后三维的那么这样定义一个坐标系有什么好处？我们就可以把任意一个向量都给分解到这三个轴上去，就是这个向量的分解。

[43:49](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=2629)
咱们刚才已经说了，这个就要利用他们的这个投影，他们的投影怎么算？就是用点击，而且这里有一个好处是u、v、 w 都是单位向量，所以他们这个一个向量投影到这个对应的这个方向上，他们的长度是多少？这个直接用点乘的结果就立刻可以得到，因为什么呢？点成，比如说 p 点成u，它是什么呢？ p 的长度点成 u 的长度再乘以 Cos Theta，但是 u 的长度偏偏就是1，所以它这个结果就是 p 的长度乘以 Cos Theta，所以正好就是它投影的长度，然后投影的长度乘上它的这个 u 方向的单位向量，就把它变成了一个在 u 方向上的投影的向量，然后 v 方向、 w 方向三个方向都是这么投影得了，三个向量加起来就是原来的向量。

[44:30](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=2670)
这就是为什么我们喜欢用这个直角的这个坐标系，因为它非常方便，对吧？那这里就是当然了另外一个点乘的一个向量，一个应用，那么到现在我看一下这个大家有没有什么这个什么问题，应该差不多，我觉得那咱们就继续，那咱们这里要再给大家提到的就是矩阵，对，那么这个矩阵这个大家可以看到几乎所有的这个计算机的课都会涉及到一些这个矩阵的一些操作，然后这个当然在大家这个可能会很头疼。但是矩阵其实并不难，咱们这个给大家说一说，特别是应用在这个这个变换上，矩阵其实挺简单的。然后这个我们这个之后会给大家特别提到说，我们如何用矩阵表示一些基础的一些变化，比如说这个移动、旋转、缩放、错切之类的这种操作。然后嗯，在图形学里，当然了这个变换就是矩阵的一个最大的应用。

[45:30](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=2730)
那么矩阵是什么呢？很简单，矩阵就是一堆数，然后这堆数把它给安排在一个这个平面上，然后这个变成一个几行几列的这么一个结构，对吧？像这里大家看到一个矩阵，这个矩阵是 3 行两列，所以是这个 3* 2 这样的一个矩阵，然后这个矩阵的一些基本操作，比如说矩阵可以乘以一个数，然后成立一个数，很简单就把矩阵里面每一个数都乘这个数就可以了。然后这个非常简单，那么咱们这个就直接忽略它，那么矩阵最困难的操作也其实最有用的操作是什么呢？是矩阵的乘积。那么矩阵的成绩，这个首先前提要求你要是给定两个矩阵，它两个必须得能成才行。那什么是这个可以成的矩阵？那就是说如果大家看这两个矩阵分别是 3 行 2 列和 2 行 4 列，如果写成这个形式，大家可以看到上面 m 乘n，然后点成，这不就是这个 m 乘 n 的一个矩阵去乘以一个 n 乘 p 的矩阵，这样乘才有意义，也就是说第一个这个矩阵它的列数必须得等于第二个矩阵的行数。

[46:42](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=2802)
然后这个我觉得这个就直接用这个几乘几这样看着最明白，就是说这个中间这个 n 必须相同，也就是这里 3* 2，那必须乘以一个 2 乘什么什么什么，在这里是 2* 4，那乘的结果其实也很明白，就是说就好像是中间这个 n 抵消了一样，就相当于变成了原来 m 乘n，然后这个这样一个矩阵乘以 n 乘 p 这么一个矩阵，那么我们就把它得到的结果就是一个 m 乘 p 的一个矩阵。然后就是有这么一个性质，那么关于这个矩阵，这个新的这个矩阵，它这个每一个元素都是什么？这个中间有各种各样不同的数学定义，也是这个地方比较容不容易记住。但是这里我给大家提供一个简单一点的技法，然后这个怎么做？那大家首先看这个例子，是 3 行 2 列 3* 2 的矩阵乘以一个 2* 4 的矩阵，那么大家知道最后得到结果肯定是 3* 4 的矩阵不会错，咱们先把这个大小定下来。

[47:37](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=2857)
那么现在我就问这么一个事情，就是说每一个元素，比如说这里大家看到这个 26 这么一个数字，就是 2 行 4 列，在这个最后结果上这是怎么算出来的？那就是这么算的，因为我要想算这个 26 是多少，他我知道我想算的是 2 行 4 列的结果，那么我们就去找第2行和第4列，分别是在两个这个输入矩阵里面找，很简单，比如说这个 26 是二行四列，那么我们找原来的第二行 5 和2，然后四列是 4 和3，那么这两个向量找到了求一个点击就可以了。比如 4 乘 5202* 3 得6，加起来26，就是这么回事。然后比如说这个，我们看这个左下角这个 8 就是新的这个矩阵左下角这个8，然后它应该是 3 行一列，那 3 行一列很简单，我们就找第三行，找第一列，那第三行是在第一个矩阵里面 0 和4，然后第一列是指这个第二个矩阵里面 3 和2，那么他们两个乘积，他们两个点击就是 3* 0 得 04* 2 得8，嗯加起来就是8。

[48:40](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=2920)
所以这样做就比较简单，就是说省得去记一系列的这个各种各样的这个复杂的公式， i j k 的什么东西不需要？咱们就利用了一下点乘的这个概念。好吧？就是记得需要算第几行、第几列，那就去找第几行和第几列就可以了。好吧，那这就是这个矩阵的成绩。那么矩阵的成绩这个有一个非常重要的性质，这个性质就是没有任何交换率。OK，所以说 a 乘以b，正常情况下都不等于 b 乘以a，有一些情况下是这个等于的，但是更通用的情况下是这两者基本不等于。所以说 a 和 b 乘a，这个两个是不能交换顺序的。但是矩阵的结合率和分配率都有，特别是什么比较有用？结合率很有用。

[49:29](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=2969)
什么叫结合率？就是a、b、 c 这个放在一块乘，那我可以先乘a、 b 再乘c，或者先乘b、 c 再乘a，只要我不涉及到把它顺序对掉这种就可以，就是说结合率是有的，就是不能交换，交换率是不行的，对吧？就这个意思，那当然这个分配率很简单，就是这个意思了，然后呢？这就是这么一个性质，然后就记得它没有这个交换率就好了。然后那么一个矩阵如何在一个特殊的情况如何和一个向量成，那就是说我认为这个向量是一个列向量，这里就有意义了，那么这里我就始终认为这个矩阵在左边，然后向量在右边，然后向量永远都是一个列向量，也就是永远都是 m 乘 1 的这么一个矩阵，然后左边这个矩阵只要它是什么乘 m 就可以，这样就可以在一块乘。

[50:21](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=3021)
那这就是最重要的核心，也就是说我们要算这个变换，比如这里可以给大家剧透一下这个，咱们下节课要给大家说这个变换。一个最简单的变化，就是说任何一个形状二维的，然后咱们要把它给按 y 轴做一个对称操作，那 y 轴做对称操作，也就是说给你任何一个x，你都得把它变成负x，那 y 的话不变，因为它是按 y 轴进行操作，也就是 x 轴在变好。那也就是说给你 x y，然后一定会这个把它给变化成负 x 和y。

[50:56](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=3056)
那么什么样的矩阵可以让 x y 变成负 x 和y，那就是左边的这个看大家看到这么一个矩阵，- 10 和 0 和 1 这么一个矩阵，大家可以乘 1 乘试试，大家就会发现这个确实是这样，那这就是一个左边这个矩阵，就是一个这个用来求这个镜像的这么一个矩阵，当然咱们之后会说的更多，好吧，这里这简单给大家提一下而已。那么矩阵还有什么什么别的操作呢？

[51:24](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=3084)
很简单，矩阵还有一些这个转制操作，咱们刚才在这个这个向量上已经说了，那就是把行和列互换，那矩阵上也一样，那么原本 3 行 2 列，那这里自然变成 2 行 3 列，那这个原本的这个 i 行 j 列变成了这行 i 列，就是把它给这个调换一下顺序。然后这个矩阵的转制有一个这个性质，就是说如果你要乘两个矩阵再转制，那就好像你先对后一个矩阵做转制，再乘以前一个矩阵做转制。所以这是一个比较有意思的现象，它这个就是说乘积的转制，你要先把它这个顺序调过来，然后分别做转制再做乘积。这里就是一个这个这和直观上并不一样的事情，就是说这里是矩阵的一个性质转制，然后另外一个给大家提了一个特殊的矩阵，叫做这个单位矩阵，然后这个单位矩阵什么意思？它是一个对角阵，所谓什么叫对角阵？就是说这个就是说只有对角线上有这个非 0 的元素在这里，这个对角线上全都是1。

[52:30](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=3150)
什么对角线？左上到右下这条上面就是说单位矩阵也分这个它的这个维度或者大小，像这里大家看到的是一个 3* 3 的单位矩阵，然后单位矩阵是什么意思？或者说它用来干什么呢？单位矩阵基本不做任何操作，比如说这个单位矩阵，咱们管它叫i， i 如果乘以a，得到的结果一定还是a，然后 a 乘以i，得到结果也应该是a，然后就它基本没用。它没用，但是可以定义下面一个式子，叫做这个矩阵的逆。

[52:59](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=3179)
矩阵的逆是什么意思？如果你能找到一个矩阵，和你原来的矩阵相乘，然后不管顺序，然后得到的结果就是得到的结果都是一个这个单位矩阵，那么我们就认为这两个矩阵是互逆的，那也就是说我们原本有一个这个矩阵a，然后它乘以 a 的逆就可以得到单位矩阵。那么当这个逆矩阵的计算和这个转制的计算其实很相似，就是说如果有乘积的逆，其实相当于先把这些这个对应的这些矩阵逆过来，然后在这个相乘，然后并且顺序是反的。这里可以看到大家先这个对 b 进行逆，然后再对 a 进行这个逆，然后再乘起来，这当然是它的一个性质。

[53:42](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=3222)
然后这个我们刚才提到说向量可以写成这个，可以有这个点乘和叉乘的操作，那么其实向量的点乘和叉乘都可以写成矩阵形式。什么意思？比如说咱们看这个点乘，就是 a 点乘， b 可以写成 a 转制和 b 的乘法，就是 a 转制。你认为 AA 如果是一个，这个原本是一个列向量， a 转制变成了一个航向量，那么这个航向量直接乘以这个列向量b，得出来的结果正好就是一个数，就是大家看航向量是多少，一行 3 列，然后这个 b 的列向量是什么呢？ 3 行 1 列，所以一行 3 列乘 3 行 1 列，一定得到 1 行 1 列，也就是一个数，所以大家在右边看到也就是一个数，没有问题。

[54:26](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=3266)
那么这个，嗯，叉乘是否能写成矩阵的形式？这个相对困难一点，但是其实是可以的，就是说我们把这个 a 向量给这个重新组织一下，写成这个 a 星号这么一个，这么一个这个矩阵，这个不是 a 乘b，这个是 a 星号，是一个矩阵，然后它乘以这个 b 向量。OK，所以这个 a 星号是什么呢？就叫做这个 Dio matrix。然后然后这个就是从 a 把它这个向量转化成这么一个矩阵，大家可以看到是怎么排的，这个 x 要排在哪儿？ y 排在哪儿？ z 排在哪儿？加什么负号。然后就是说通过这个矩阵乘以这个 b 向量得到的结果，就是这个叉乘的结果。唉，我们为什么要这个东西？就是说我们也之前有 a 和 b 的话，我是直接是可以算这个这个叉乘的，我们之后会看到在一个旋转上面，这个这个旋转的一个推导，上面这一步是其实挺有用的，也就是说在这里大家知道说这个向量的乘积也可以写成矩阵形式就可以了。

[55:27](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=3327)
那么给大家看一个例子，这个例子就是这个一个运动着的相机，一个运动着的相机，然后在一个这个某一个场景中间，这个场景还是很有名的，叫做Sponsa。

[55:41](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=3341)
如果大家做这个这个 render 云做一点点，大家会知道有这么东西，然后他这个相机在这个场景中任意移动，然后大家可以想象一下这个相机，你看可以往各个不同的方向看，所以说涉及到旋转，对吧？然后它又可以往各个地方不同地方走，所以如何去定义这个相机，如何去运动，那自然就是涉及到我们的这个各种各样不同的这些变换，咱们要把它合在一块，那这就是说之后要给大家讲的内容，然后呢？到目前为止，嗯，好，OK，OK，好像大家这个没说什么，太那个的问题哈。噢，我明白了，有同学这个反映了一个事情，说这节课挺简单的，没问题，大家说的太对了，这节课非常简单，可是在 3 节课之后就会变得非常困难。好吧，大家知道有这么一个事情就好。然后就是说咱们由浅入深的说嘛，先把这一块简单的东西说明白，但是一定要相信我这课，这个只会越来越难好吗？这个这节课简单是对的，就是给大家复习一下，给告诉大家一个信息，这个线性代数，特别是咱们图形学上要用的线性代数，基本就到此为止了，到这儿就等于是就已经够了，为了学习后面的这个图形学的内容。

[57:03](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=3423)
所以我觉得如果大家觉得这个课这节课简单，那就太好了，没有什么问题，就等于是咱们把这个先行代数复习一遍，然后咱们之后这个下节课开始，到下节课咱们会讲更多的内容，比如说咱们会提到这个二维的旋转，然后不二维的各种各样的变换。然后以及说我们要开始提到一个叫做这个，这个我想一想中文应该叫，嗯，中文应该叫什么呢？这样吧，我请同学帮我翻译，我要这个跟大家说的一个概念，叫做 homogeneous coordinate，然后这个大家有知道的吗？这个应该翻译成什么？我来关注一下。

[57:55](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=3475)
对，其次坐标，对对对对对，就是这个，然后这个涉及到这块就会渐渐的开始会变得这个稍微麻烦一点，然后这个之后这个咱们慢慢的把这些事情都给说明白，好吧，希望大家之后的这几节课都会觉得跟这节课一样简单，那就成功了好吗？那咱们下一节课就会开始说transform，好吧？当然了，不是变形，而是变坏，好吧，那咱们这个这节课，哎，时间正好。

[58:25](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=3505)
那咱们就说到这里，好吗？感谢大家，然后之后希望大家继续支持，我也希望把这个课，这个每节课都说这么简单，那就好了，好，OK，对，还有一个事情，这个我在想我现在在麻烦我们的助教同学试图做一个这个作业 0 的框架。大家知道我们有那么多次作业，然后就是说我希望大家上手作业 1 的时候要相对容易一些，所以大家这个准备一个作业0，所谓作业 0 其实并不是这个一次什么作业，就是大家把这个环境配起来，这个就算是作业 0 了，没什么事情，就是说这样呢，提早也可以给大家放出来这个虚拟机和这个对应的用法。

[59:07](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=3547)
大家也可以熟悉一下 visual studio code 的是一个怎么样的这个运作方式，然后之后大家写代码怎么做，就总之作业 0 没有任何实质内容，就是给大家上上手好吗？那就是这么一个事情，然后对这个之前提到这个，如果有时间咱们说一说变换，看来是没时间了，那咱们下节课再继续做好，同样这个课程结束之后官网会有录播，然后我也会立刻把这个课程的这个 PDF 对应的讲义，然后放在我们的课程网站上，好吧？那就这样，之后咱们这个下节课再见。

[3:06](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=186.481115)

# 图形学依赖的基础科学

[3:51](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=230.53687)

# 这节课的内容

[5:52](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=352.160903)

# 例子

[6:44](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=403.912882)

# 向量基本概念

[7:41](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=460.680587)

## 向量归一化

[9:47](file:///Z:\阿里云盘\技术美术\GAMES课程\GAMES101-现代计算机图形学入门-闫令琪\Lecture_02_Review_of_Linear_Algebra.mp4#t=587.025764)

$\hat{a}$  读作 a hat

## 向量求和

[11:18](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=677.8148)

将 $\vec{a}$ 与 $\vec{b}$ 首尾相接就可以得到相加之后的结果

## 笛卡尔坐标系 Cartesian Coordinates

[13:22](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=802.102978)

向量的书写方式，默认是列向量（缺省值），哈哈哈哈

# 向量乘法

[16:32](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=991.776762)

## 向量点乘

[16:37](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=997.486221)

### 概述

[18:12](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=1092.298962)

### 点乘的性质

[19:34](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=1173.609523)

### 点乘的计算

[20:30](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=1229.582043)

### 点乘的应用

#### 计算得到两个方向之间的夹角

[21:50](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=1310.183806)

#### 计算一个向量到另外一个向量的投影

[22:28](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=1348.369125)

#### 计算两个向量的相近程度

[25:43](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=1543.499613)

#### 计算两个向量的方向是相同还是相反

[25:60](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=1559.631683)

## 向量叉积

[30:21](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=1821.023224)

### 叉积的性质

[33:33](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=2013.3814)

[34:14](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=2054.372476)
如果在三维坐标系中，x 和 y 的叉乘得到的是z的话，那么就说当前的坐标系是右手坐标系

[35:10](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=2110.274831)
所有的叉乘结果都是向量

### 叉乘的计算

[36:02](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=2161.923607)

### 叉乘的作用

[37:07](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=2226.978795)

#### 判断一个向量在另一个向量的左边还是右边

[37:32](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=2252.020002)

#### 判断一个点在三角形的内部还是外部

[38:55](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=2334.624236)

# 正交系 / 坐标系

[42:54](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=2574.484146)

## 定义

[43:15](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=2594.78646)

# 矩阵

[44:51](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=2691.457573)

## 矩阵是什么

[45:32](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=2731.929046)

## 矩阵乘法

[46:03](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=2763.304142)

## 矩阵乘法的性质

[49:03](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=2942.826816)

## 矩阵与向量相乘

[49:59](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=2999.027405)

矩阵和向量相乘时，认为向量是一个列向量并乘在矩阵的右边。

## 矩阵的转置

[51:24](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=3083.514619)

矩阵也有转置，并且矩阵乘法转置满足  $( A B ) ^ { T } = B ^ { T } A ^ { T }$

## 单位矩阵和逆矩阵

[52:13](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=3133.454388)

# 向量乘法 矩阵的形式

[53:44](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=3224.462149)

# 变换的例子

[55:32](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=3331.820319)

# 提问

[56:18](file:///Z:/阿里云盘/技术美术/GAMES课程/GAMES101-现代计算机图形学入门-闫令琪/Lecture_02_Review_of_Linear_Algebra.mp4#t=3377.735645)