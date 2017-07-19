---
title: 前端学习【工具篇】——工欲善其事，必先利其器
date: 2017-04-13 07:03:31
tags: 
- 前端
- 学习笔记

categories: 编程
---

作为前端入门新手，如何找到一款称心如意的编程工具是至关重要的。今天，笔者就来安利介绍一些能够大大提高你前端编程效率的编程工具！

<!--more-->

## 安装IDE

首先你需要安装一款IDE。

>个人推荐**Node.js环境下的Sublime 3**

首先，让我们打开Sublime，新建一个demo.html文件愉快的在代码区域中输入 `！`


![在Sublime中输入`！`](http://upload-images.jianshu.io/upload_images/2141706-d8643aad3d99e232.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


对，你没看错！赶快输入  `！`吧~ 

然后按下快捷键 `Ctrl + E`
![按下快捷键 `Ctrl + E`](http://upload-images.jianshu.io/upload_images/2141706-21ad7e1629fd300b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


奇迹发生了！
sublime竟然自动生成了html的骨架！
与此同时，我们愉快的前端程序猿之路也正式开始了！

## 安装插件

接下来，我要给你强烈安利几款sublime功能强大的插件。
但是，在这之前我们先来学习一下如何在sublime中安装插件。

首先，按下快捷键 `Ctrl + Shift + P`

![输入`Ctrl + Shift + P`](http://upload-images.jianshu.io/upload_images/2141706-93b770dd9a999796.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
你会发现屏幕上弹出了一个下拉搜索框。

接着，输入`INSTALL`，并点击回车

![输入`INSTALL`](http://upload-images.jianshu.io/upload_images/2141706-bc9d90208699a28a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![输入回车](http://upload-images.jianshu.io/upload_images/2141706-073d266bf8d7eb2a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
这样就会弹出可安装插件的搜索框，然后你就可以愉快地在搜索框里输入你想要安装的插件并敲下回车进行安装了。（插件安装时间非常短，可以在sublime的左下角看到短暂的安装信息。等插件安装完成之后一般就会弹出插件的说明文本。注：部分插件需要**配置node.js的路径**。下面会就具体插件进行举例。）

最后**重启sublime**，然后你就能正常使用该插件了。是不是非常简单呢？没错，这就是我向你们强烈安利sublime的原因。

## 重磅插件推荐


#### Emmet插件（[官方文档](https://docs.emmet.io/)）
>Emmet is a web-developer’s toolkit that can greatly improve your HTML & CSS workflow.

Emmet的前身为 Zen Coding，如果你从事过前端相关工作，那么你对它一定不会陌生。其采用了**仿CSS选择器的语法**将你输入的代码片段生成为完整的HTML或CSS代码，极大的提高了代码的编写速度。

![Emmet](http://upload-images.jianshu.io/upload_images/2141706-67f583582651ddbf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### 一、安装
 
- 输入`INSTALL`，并点击回车

![输入`INSTALL`](http://upload-images.jianshu.io/upload_images/2141706-bc9d90208699a28a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 输入`Emmet`，并点击Emmet Css Snippets进行安装

![点击Emmet Css Snippets](http://upload-images.jianshu.io/upload_images/2141706-c294ee85cf54b996.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 点击`菜单栏>首选项>插件设置>Emmet>Settings-Default`可进行相关设置 

![Emmet设置文档](http://upload-images.jianshu.io/upload_images/2141706-15d81aa9f2fd9cbb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
正常情况下，该插件不需要配置路径，只需**重启sublime**即可使用。

##### 二、使用

>Emmet的快捷键是Tab，有点类似于sublime自带的智能感知，但是需要在你输入代码片段后按下Tab来触发。
 
下面我来举一些**HTML**中例子：

- 首先我们还是用 `!` 来举例子，和之前没有安装Emmet会有什么不同吗？

![输入 `!` ，并按下Tab](http://upload-images.jianshu.io/upload_images/2141706-21ad7e1629fd300b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

和之前完全一样，有木有！不同的是我们现在只需要按一下Tab键，不需要费力地用手去够快捷键了。

- 输入`ul>li*6`，按下Tab

![`ul>li*6`](http://upload-images.jianshu.io/upload_images/2141706-63a491b6e0c8ad20.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

Boom！！！一个原本需要费劲的敲很久的列表标签就生成了！

- 输入`div.foo>h1`，按下Tab

![`div.foo>h1`](http://upload-images.jianshu.io/upload_images/2141706-fb88a4e99494239c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

一个class为foo，并且嵌套着一个h1标签的div标签就这样瞬间生成了！

- 输入`(div.foo>h1)+(div#foo>img)`，按下Tab

![`(div.foo>h1)+(div#foo>img)`](http://upload-images.jianshu.io/upload_images/2141706-40eea27c52c2dbc7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

想想我们可以为此节省了多少时间？是不是有点小激动呢？

然而Emmet的强大绝不仅限于**HTML**，下面我再来举一些**CSS**中的例子：

- 输入`w100`，按下Tab

![`w100`](http://upload-images.jianshu.io/upload_images/2141706-7bdfa183dcee503b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 输入`h75p`，按下Tab

![`h75p`](http://upload-images.jianshu.io/upload_images/2141706-3295f902f49be802.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 输入`ov-h`，按下Tab

![`ov-h`](http://upload-images.jianshu.io/upload_images/2141706-6f4a4c050864a807.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**是不是感觉酷毙了！**

由于篇幅关系，笔者在这里仅仅举出了一些简单的例子，目的是让读者能对Emmet插件有个大概的认识。这个插件的优点就是上手极快，可以充分发挥自己的想象力，大大提高码代码的速度。你还在等什么，快去试试吧！

#### CSSComb插件（[官方文档](http://csscomb.com/)）
>Makes your code beautiful

这款插件可以使用指定的排序方式对CSS的属性进行排序，使你的CSS代码更加规范

##### 一、安装

- 输入`INSTALL`，并点击回车

![输入`INSTALL`](http://upload-images.jianshu.io/upload_images/2141706-a63328f1e3e5fab5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 输入`CSScomb`，点击安装

![输入`CSScomb`](http://upload-images.jianshu.io/upload_images/2141706-74b080e7f877f38c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 点击`菜单栏>首选项>插件设置>CSScomb>Settings-Default`，将里面的**"node-path"属性**设置为你电脑上node.js的安装路径即可

![修改路径](http://upload-images.jianshu.io/upload_images/2141706-9ffd066e90c13753.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 最后一步，**重启sublime**

##### 二、使用
>右键 run CSScomb 即可


![使用前](http://upload-images.jianshu.io/upload_images/2141706-2d9cf2d510000c74.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![使用后](http://upload-images.jianshu.io/upload_images/2141706-6c4e0e285119a236.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

效果还是很明显的~


#### CSS Format插件
>强大的CSS格式工具，有多种格式可供选择

##### 一、安装
>与上面的插件安装步骤完全一致，后面不再放图

- 输入`INSTALL`，并点击回车

- 输入`CSS Format`，点击安装

- 不需要配置路径，**重启sublime**即可

##### 二、使用

- 右键 CSS Format >Expanded （注意，与CSScomb不同，不会改变CSS属性的顺序）

![Expanded](http://upload-images.jianshu.io/upload_images/2141706-ad1d3e0a6cfead1d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 右键 CSS Format >Compact

![Compact](http://upload-images.jianshu.io/upload_images/2141706-b9d594e7018b2a4c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 右键 CSS Format >Compressed (一行CSS代码）

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/2141706-d83271d9c3f5fdd4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### HTML-CSS-JS Prettify插件

最后来讲一讲前端通吃的格式优化插件 HTML-CSS-JS Prettify

##### 一、安装
>与上面的插件安装步骤完全一致，后面不再放图

- 输入`INSTALL`，并点击回车

- 输入`CSS Format`，点击安装

- 需要配置路径，将你电脑对应系统的路径改为node.js的安装目录保存即可（对了，在sublime中保存的快捷键为`Ctrl + S`）

![路径配置](http://upload-images.jianshu.io/upload_images/2141706-058608927f69a982.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 最后**重启sublime**即可

##### 二、使用

使用方法和前面的类似，也是右键选择即可。这款插件除了能够修改CSS的格式外，还能修改HTML与JS的格式。但需要注意，这款插件也不能改变CSS属性的顺序。


>小结：笔者一口气给大家安利了4款比较常用的插件，部分插件的功能可能存在重复，但是我们可以各取所长。比如，**对于CSS文件一般可以先用CSScomb调整CSS属性的顺序，然后再用CSS Format转化为自己想要的格式。对于HTML和JS文件，我们则选用HTML-CSS-JS Prettify插件。**

## 结语

>工欲善其事，必先利其器。

掌握了上述IDE以及插件，那么你的前端之路想必已经有了很好的开端。笔者想要告诉你的是，虽然已经有了一把得心应手的武器，但是前端学习之路才刚刚开始，多动手多打怪才是提高编程能力的不二法门。加油吧！骚年！
