---
published: 2024-07-02 15:29:45
author: 枣把儿
title: 当一个程序员突然想做一款产品
description: 你一定有很多瞬间，脑子诞生了一个有趣的产品雏形，但因为种种原因搁浅，最终没有落地。
category: 早早集市
tags: [产品, 早早集市]
---


你一定有很多瞬间，脑子诞生了一个有趣的产品雏形，但因为种种原因搁浅，最终没有落地。

## 引言

在一个普普通通的周二，我又㕛叒一次萌生了和许多程序员一样的想法：做一款自己的产品。

鉴于以前的想法 99% 都变成了一个一个不能用的 demo，还有 1% 在反复起步，这次我痛定思痛，决心一定要好好“架构”一番！！

## 起步

说干就干。我熟练的打开Obsidian，打开Excalidraw 新建绘图，开始设计网站的草图，然后在一旁开始罗列想用的技术栈、表结构、功能点。一阵奋笔疾书后，一个网站的大概样子已经尽收我眼底！

![zz-pp-1702258999712.png](http://img.zzstudio.cn/zz-pp-1702258999712.png)

正当我心中一阵窃喜时，我突然意识到我还缺一个Logo。

是的，这是一个非常严重的问题。虽然我还没有新建文件夹，但是这种建成后必定一流的网站要有一个配得上它的一流Logo才对。不行，我一定要为它找一个称心如意的Logo才行。但是今天已经快下班了，我只能明天再搞了。

ok，愉快的第二天马上就来了。

我开始从AIGC和自主设计两个方向寻找适合我的Logo，很快啊，AIGC被我排除了，因为它感觉就像一个不合格的Tony老师一样，不适合我这种精益求精的态度。

于是我打开b站，开始观摩几个设计领域的大up主，看看能不能吸取到一星半点的灵感（当然是只感受到了nb二字）。突然，我发现了一个[搬运自YouTube的视频](https://www.bilibili.com/video/BV13U4y1u7zB/?spm_id_from=333.999.0.0\&vd_source=cf9b3c8faa56d0c64b09a55be382ef80)，再结合之前我在[pinterest](https://www.pinterest.com/)看到的让我眼前一亮的像素风格，就决定是你了！！

![touxiang](http://img.zzstudio.cn/touxiang12.jpeg)

## 再起炉灶

我打开了我珍藏已久的Adobe AI , 想尝试按视频里的操作自己设计一番，但无奈它提示我因为某些原因不能继续使用了，并且只给了我退出软件和购买软件两个选项。我在微信提示余额不足后咬牙选择了退出。

既然如此，我只能自己先实现一个生成LOGO的工具了。（是的，像擦出爱情的火花一样突然）

（至于最开始是想做什么产品，我先按下不表）

## 功能构思

在分析了视频里的操作方式后，先在脑子构思一些这个小工具具体实现的功能：

*   一个可拖动的画布
*   一个可绘制的区域，区域内由带有黑色边框的小方格组成，并且可缩放可拖动。
*   小方格可以设置数量，如：100x100，单个方格可以设置大小，如格尺寸为：5x5
*   绘图模式下，鼠标可在绘图区域的小方格上点击并滑动，小方格会被设置对应的颜色
    - 颜色可配置，并且方便切换：比如tab键自动轮换预制的几种颜色
*   绘制后，图片可导出
    *   导出时，去除黑色边框？
    *   导出时，去除未涂色的方格？
    *   导出时，批量设置未涂色的方格颜色？
    *   导出时，压缩图片？
*   导入一个图片，分析图片的像素值，自动绘制到画布上
    *   图片要不要限制大小？
    *   导入的图片在前端分析还是在后端分析？
    *   在后端分析的话，如何设计一个上传接口，且避免自己的服务器被挤爆？
    *   分析一个图片像素分布的插件、算法是不是已经有类似的库可以直接拿来用？
    *   如果自己手写一个分析像素值的功能，如何设计采样的步长最合理，最高效？
    *   ~~不会已经有AI可以直接替代我这个产品了吧？~~（想到这里，我狠狠的打了自己一个大嘴巴子！想起了以前各种没出世的小产品，我决不能再找到一个理由不去完成这个产品）

构思到这里，我已经可以在脑子里完整的走完【生成像素LOGO】这个功能。

这算是一个产品经理立项的过程了，先聆听客户需求-> 再分析和拆解-> 以一个产品的形态实现客户的需求-> 梳理成文档发给研发部门或开项目启动会

后面可能还会有交底、反交底、UI评审、测试用例评审等等会议，这里出于产品本人即是UI又是开发，在大家的一致赞同下就跳过了。

## 技术栈选择

围绕着这些要实现的功能，我作为一个开发，首先想到了两种方向：

第一个是原生dom。

没错，在这个卷虚拟dom卷的没边儿的年代，我还能想到用原生dom来实现这个功能，实在是不忘初心，值得一个点赞和关注。

绘制方格、鼠标事件、控制涂色、导出图片，这些看起来都不是问题。

问题是：怎么控制这多dom一起缩放和拖拽？

由于感觉实现起来比较繁琐，不够优雅，加上这方面没有经验，以免被不能解决的问题卡住。

我开始思考第二个方向：Canvas。

先找别人做好的轮子。
1.  Fabric
2.  Konva
3.  Pixi


在经过不长时间的google之后，我分别尝试了这三个插件，且看到了一个关于这种canvas库的性能对比网站。最终选择了[Konva](http://konvajs-doc.bluehymn.com/docs/index.html)。

因为它内置了图层、图形、选择、变形、拖转、鼠标事件、导出图片/json等常用功能，比较是最贴合我的需求的，并且中文文档和英文的Api文档还算友好。

关于性能，这是一个在技术选型时经常提到的问题。但事实就是，不是每个产品的量级都会发展到那么大，你在考虑几万、几十万、几千万用户或者多么多么复杂的渲染场景的时候，却连第一个真实用户都还没有？更何况我这是个没人用的工具(⊙︿⊙)

**为不存在的用户绞尽脑汁的进行性能优化，不如先为第一个用户实现主体功能**

毕竟后续的优化也是KPI嘛

解决了核心库的选择，剩下的就是围绕项目搭建所用的技术了
### 前端

前端技术的选择，秉承着用新不用旧的原则，全部用最新的技术栈，也不考虑兼容问题。所以我选择了以下技术：

*   [Vue](https://cn.vuejs.org/) 3.x
*   [Vue-router](https://router.vuejs.org/zh/) 4.x
*   [Vite](https://cn.vitejs.dev/guide/)4.x
*   [Pinia](https://pinia.vuejs.org/)
*   [TailwindCss](https://www.tailwindcss.cn/docs/installation)
*   [Konva](http://konvajs-doc.bluehymn.com/docs/index.html)

### 后端

既然是大前端，肯定优先选择Node，尽量把JS玩明白。

因为它的应用场景不光是页面或者Api服务，还包括客户端、命令行、各类编辑器插件、某些写作软件的插件、浏览器插件、爬虫、自动化等等。熟练后，使用范围非常广，可玩性非常强。

并且，司以为，业务层注重的应该是业务逻辑、思维逻辑，并不是你选了什么编程语言做后端，就可以避免屎山代码，就比别的语言优雅。

所以Node作为一个链接数据库和前端/客户端，提供一定量的稳定服务的编程语言，对我来说足矣。

再插一嘴选TS还是JS的问题，除了核心问题和选什么语言一样外。在工作上保持一定的挑战性对个人的成长很有帮助，所以建议还想成长的前端er，无脑选TS，**走在薪资的前沿总是没有错的**。

*Node版本选择：*

我目前是16.20.2 ，16的稳定版， 18、 20 也是可以的，我记得Vite5已经不支持低于18的版本，所以家里有条件的可以直接从20用起了。（偶数版本是稳定版）

*Node框架选择：*

[Nest](https://docs.nestjs.cn/) ：Node框架的不二之选。搭配[TypeScript](https://www.tslang.cn/)使用，既能学习到后端业务如何设计，又能参考目录接口如何设计，又能感受和使用TypeScript，一石三鸟。


![Pasted image 20231210213105.png](http://img.zzstudio.cn/verysix.jpg)

### 服务器

[阿里云服务器](https://www.aliyun.com/daily-act/ecs/activity_selection?spm=5176.28508143.J_ahRFo5CaAe_asSOaCgS4J.7.5421154akYLvYx&scm=20140722.M_169282029.P_163.MO_2275-ID_10071131-MID_10071131-CID_30876-ST_9367-V_1)，前一阵搞活动99元/年，还是很划算的。

牵扯到的备案、域名、Nginx+Https，后续上线篇会展开讲讲。

### 部署方式

[Docker](https://www.docker.com/)

用docker跑nginx、redis、mysql，这样本地和服务器环境能尽量保持一致，还能提前验证问题。不至于本地开发完没问题，部署上去又出现各种问题

至此，一个从产品立项、到技术选型、最后到运维部署的流程已经梳理完成。下一步就是具体实现各个功能了！

## 小结

源于一个突发的灵感，在纠结了它到底对谁有用之后，我决定先上手实现它。

也许功能对其他人没用，但记录和写作的过程对我很有用。

如果对新入行的同学，也能有一点点启发和带动作用，这将是我继续写下去的最大动力。

喜欢的朋友可以点个关注，继续追更后续的技术篇。有任何前端问题想要咨询的同学，也欢迎加VX：zzdaddy7，我会尽力为你解答。

感谢你的阅读，我是枣把儿\~


