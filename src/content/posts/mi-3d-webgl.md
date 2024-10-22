---
title: 当一个程序员看到小米汽车发布后，竟然产生了这样的连锁反应
description: '...'
author: zzdaddy
published: 2023-12-11 00:00:00
tags: [吐槽, 程序员]
category: 生活
---

# 1 

最近被铺天盖地的小米热搜给包围了

不得不感叹，雷总的营销手段之高，网上的曝光量如此之大，小米汽车到位之后，想去试驾的人也一定少不了

试驾的越多，只要车没啥大毛病，购买率就越高

况且现在汽车行业的各项指标都是有数的，小米只要对标着来就错不了，真正的买车的主力，估计还是没那么了解汽车的群体

外观漂亮，机械素质高，驾驶感优秀，再来点智驾功能，价格只要在购车人群的预算内，很难说会越过小米汽车

不管怎样，对于一个消费者而言，还是很看好小米汽车的，希望早日让汽车的性价比提升到和小米手机一样的高度

# 2

虽然小米汽车热度很高，但程序员嘛，在公司摸鱼还是以摸文字版的信息为主，不敢太过造次

再个，程序员摸鱼的论坛，多少还是和微博这类阵营有点区别的，也不仅仅是热点新闻

这不，前几天我就看到了一个关于小米汽车的3D网站，打开网站一看，好家伙， 我直呼好家伙

![](https://img.zzstudio.cn/1-img-20240401160451.png)

这效果，你说这是小米花钱打造的我都信

太丝滑了实在是

顺着网站的介绍，又摸到了作者的其他作品，还有网页版原神，以及一个杭州亚运会水墨风宣传片

好家伙，是个真大佬

把玩了大佬的作品之后，感觉整个人都被点燃了，什么时候咱也能搞出个这个来啊!!

此刻我的身体已经开始发热，感觉血液已经冲上了脑门

**仿佛鸣人在变身九尾**

**艾伦在变身巨人**

**大古在变身奥特曼**

**耐摔王正在以雷霆击碎黑暗**

**战斗!!!  爽!!!  **

我必须马上开始学习webGL!

# 3

说搞就搞，我立马就打开了vscode，准备开始我的webGL学习之旅

目前用的最多的就是Three.js这个库了，那我就从它开始搞起

先找到官网，快速过一遍Api，了解一下基本概念

过完了，直接开始手搓!

不会也没有关系，现在有了AI辅助，在完全不懂的情况下，完成一些demo也不是问题，这里我用的是月之暗面的Kimi

先给AI设定一个背景，然后表达出自己具体的需求，比如，我就是想用threejs加载一个3d模型，然后给3d模型尝试换色

先根据官网，把项目搭建起来，然后根据Kimi的提示，一步步的完善代码

很多像是做着色器/uv/shader这些名词，不懂也不用先深究，目的是先搞个3d模型出来让自己爽一爽

看文档得知，3d模型推荐使用glsl格式的模型，于是我先去找一个3d模型下载到本地来

找到了一个 [3d模型网站](https://www.turbosquid.com/)，然后选择免费的模型，大佬搞个小米su7，咱也别太差，弄个奔驰大G就行

然后把尝试在代码里把模型加载进来

当然，这期间不是这么顺利的

其中很多坐标系问题，模型加载不顺利，灯光忘记加了，摄像机位置不对 这类问题就一一对照官网文档和AI的提示，也没有花费太多时间就搞出来了

![](https://img.zzstudio.cn/1-img-20240401160481.png)

模型加载出来之后，我先尝试给模型换一个颜色，在AI一遍一遍的提示下，始终无法做到像是真实世界汽车改色一样的效果

我就怀疑是不是我的模型有问题，因为我看到3d模型的文件里，只有一个mesh，只要一改颜色，就整体全部都改了，改完的颜色就像是在ps里给他硬生生叠加了个颜色上去一样

![](https://img.zzstudio.cn/1-img-20240401160403.png)

但是我又对3d模型里的各种专业名词不太了解，只靠自己猜测，恐怕解决不了这个问题

而且用AI把控大方向的编码是没问题的，太具体的需求它也解决不了，除非把所有关联的上下文全都喂给他，但是这样又不太现实

于是我就找了个搞3d的老哥请教了一下，大概了解到了，如果要精细的实现控制只在某些部位比如车身上变换颜色或者痛车，模型就得分为多个mesh才行

而要实现精细的特效，多半要自己手动实现shader，只用threejs可以实现一些的效果，但达不到自定义的高度

好吧，看来是要继续深入探究了，不过这不也是开了个头嘛~

# 4

既然需要shader，我就去了解了一些shader的概念，以及一些shader的教程，先让自己对shader有个大体了解

一顿恶补之后，好歹知道了顶点着色器以及片段着色器的概念，这时才知道Kimi给我写的材质里传入的那一堆代码是什么东西!

但这类野文十分稀少，连掘金小册都只有一本

为了便于让自己更好的学习shader，我就花了十来块钱，买了小册，利用上班时间和业余时间，闲里偷忙，开始跟着作者实践起来

学习新东西，还是尽量找到一些别人总结好的教程，不管是付费的还是免费的，只要是总结成体系的，肯定是比刷野文要吸收的好一些

大概花了两天的空闲时间，我刷完了这本小册，对于一个数学已经忘得一干二净的人来说，还是十分烧脑的

但我还是硬着头皮把它看完了，倒不是说完全学会了其中的各种函数，这毕竟是有数学门槛的，但我只需要理解什么时候要用，能实现什么效果即可

而且作者的实战项目里，还会教一些他在用的框架，vscode插件等等，这些东西如果靠自己搜，估计很难搜到

所以说，找一份别人提炼过的教程来学习，事半功倍，能接触到不少相关的库和技巧

小册最后，作者也推荐很多shader的相关学习资源，正好我还不理解的部分也想着继续深入学习一下，于是我就一一打开看了看，尝试了一下工具，收藏起来

然后我就发现了Essense of Linear Algebra 这个视频，b站叫 [线性代数的本质](https://www.bilibili.com/video/BV1ys411472E/?vd_source=cf9b3c8faa56d0c64b09a55be382ef80)，因为shader计算的背后是线性代数这门学科，这个教程以可视化的方式很形象的阐述了线代的主要知识点(向量/矩阵等)

本来我没想着从头再学一遍线代，但是我还是打开看了看

这一上来还没看到内容，弹幕的夸赞就让我知道，可能是捡到宝了!

# 5

我的目的是理解线代和计算机图形学的关系，同时帮助我加深理解那些sdf函数是如何产生神奇的效果的，而非真的去学习`计算`的那部分

这个教程真的很符合我的需求，让计算机去做计算那部分，我又不需要考试

![](https://img.zzstudio.cn/1-img-20240401150424.png)
![](https://img.zzstudio.cn/1-img-20240401150436.png)

目前这个系列我还在不断地学习中， 作者的教学及动画也正如他所说的， 让我对于这些概念有了非常直观的概念。

视频真的非常优秀，感觉刚上大学，或者上大学前，非常有必要提前看一看这个视频，对学习会很有帮助

结合之前在shader小册里学的东西，能够更好的理解shader中这些数字的运算是如何对应到屏幕上的颜色的，以及为什么产生了这样的效果

# 6

btw，整个连锁反应，没有超过三天，并且还是在工作日。

因为一个炫酷的网站，真的学到了很多自己未知领域的东西，技术果然还是一如既往的好玩！想必这就是最初做技术的初心和乐趣所在吧。

但是话又说回来，这三天的收获也可以说什么都没有。

因为threejs只是开了个新建了个项目，shader也玩不了6，线代也考不了高分。

Math.floor(技术方面)确实是毫无收获。

但是我又一想，也许这种学习和挖掘的能力对我来说更重要，之所以感觉没用，是还没把它用在更多或更该用的地方。

简单来讲，就是还没靠技能赚到钱，钱对人的激励永远是最大的。


那就继续探索和努力吧。






