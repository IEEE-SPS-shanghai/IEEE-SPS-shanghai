---
title: 【面向ACG编程】连续改造2个Vue网页
date: 2017-07-30
tags:
- 前端学习
- vue
- github
- ACG

categories: 编程
---

> 本文首发于掘金，如需转载注明出处。


记得阴明在vueconf上说过：抱着一种解决问题的态度去学习知识是最有效率的。作为一名小白，之前学习Vue总是被动的，规定每天看一点文档，写一点代码。总觉得不得劲。于是就想能不能给自己定个小目标，用Vue做他个网站！

移动端网址：[https://justice-eternal.github.io/](https://justice-eternal.github.io/)
PC端网址：[http://lightmoon.pw](http://lightmoon.pw/)
曲库地址：[https://github.com/zytx121/justice_eternal/issues](https://github.com/zytx121/justice_eternal/issues)

## 曲谱库的建立

后来偶然看到了[BGAIssueBlog]([http://www.bingoogolapple.cn](http://www.bingoogolapple.cn/))，觉得很巧妙的利用了GitHub提供的issue的api，比单纯的md博客更具功能性。下面是作者列出的通过 Issues 记录学习笔记的优点：

>  - 在线编辑和预览，随时添加和提交（不用担心电脑坏了导致笔记丢失）
>  - 当笔记里到嵌套图片时，支持粘贴屏幕截图和拖拽添加图片
>  - 带有搜索和排序功能
>  - 可通过 Label 来对 Issues 进行分类
>  - 可以把每一个 Comment 作为一个小的知识点不停的追加到 Issue 里
>  - 结合 GitHub Pages 绑定域名来搭建个人博客站点
>  - 于是就想能不能用issue的特性做一个比较新奇的网站呢？

然后我就开始想啊想，怎么想都想不出什么好点子。一天，和往常一样上山跑步的时候，跑着跑着突然灵光一闪，想到了自己关注的 [Justice_Eternal 口琴吧](http://tieba.baidu.com/f?kw=justice_eternal&fr=home)！一个口琴大佬云集的贴吧。该吧有大量的口琴大佬义务扒取各种新番ACG的谱曲并发布在贴吧里。大量的谱子分散在各个贴子里面，如果能够将这些谱子集中起来保存，岂不是查找的时候很方便？于是回到家后，我立马去贴吧逛了一圈，发现已经有了一个利用wordpress做的谱曲资源站，里面已经对进行了曲谱精心的分类。但是该站是租用的服务器，对于一个贴吧来说，网站的运营成本无疑是最大的问题。要知道，该站基本上是靠贴吧的各位捐款才勉强维持下来的。这更加坚定了我推行github曲谱库的决心吧！

随后我又自己分析了用issue实现曲谱库的优点：

>  - github仓库完全开源，拥有github完善的API支持，相比于封闭的wordpress数据，更利于曲谱数据的保存与调用
>  - 同样的原因，每个人的博客或者网站都能自由调用曲谱库中的数据！赛高！
>  - github-pages建立的网页完全免费
>  - issue自带搜索和排序功能，能够实现特定乐谱的搜索
>  - issue有自己的Label系统，能够对谱曲按照首字母等标签进行分类，方便查找
>  - 将每个issue的title定义为一个作品的名称，后续可以通过comment添加该作品的谱曲
>  - 可以将利用project为部分issues创建特辑，如：LL大法
>  - 用户可以利用issue的comment功能进行评论，交流吹奏心得，放置吹奏录音或视频链接
>  - 用户能够在线编辑和预览上传的谱曲，并在发布后随时修改
>  - 支持复制粘贴和拖拽添加曲谱的封面图片
>  - 因为是境外服务器，一些有擦边球行为的动漫图片不会被墙（你懂的），大量galgame谱上线中。。。

完美！！！

然后我参考moeje.org这个wordpress网站的谱曲格式写了个`ISSUE_TEMPLATE.md`文件，放在网页根目录的`.github`文件夹里。

```
<!-- 
上面的Title请务必填写谱子出自的作品名！
上面的Title请务必填写谱子出自的作品名！
上面的Title请务必填写谱子出自的作品名！

只有当第一次提交一个新作品的谱子时，才需要新建一个new issue和填写Title！
因为一个作品（issue）下面可以提交（comment）多次谱子，所以之后每次该作品的谱子只需要在相应issue下以相同格式comment即可。comment时可以将issue模板复制，选择Add a saved reply，保存为自己的回答模板。

-->

# 谱曲名称（替换）

<!-- 歌曲配图  复制粘贴到该处即可 -->


## 歌曲信息

- ![](https://img.shields.io/badge/专辑-未知-ff69b4.svg)
- ![](https://img.shields.io/badge/作词-未知-orange.svg)
- ![](https://img.shields.io/badge/作曲-未知-blue.svg)
- ![](https://img.shields.io/badge/编曲-未知-brightgreen.svg)
- ![](https://img.shields.io/badge/歌手-未知-d6504f.svg)


## 谱

【```】

谱子示例
#1#2#3#2
#1#2#3#2
#1#2#3#2

【```】

[![](https://img.shields.io/badge/扒谱-@扒谱大佬的ID-ff69b4.svg)](扒谱大佬的贴吧url)

<!-- 

[^_^]:
      请严格遵守上述格式提交曲谱，如果不符合规范，作者有权将其删除。
      如果链接出错请检查是否有空格，有的话请删去。
      如果信息缺省，删掉对应代码即可。
      ps. 如果有什么想说的话可以写在最后，但不能影响上述格式。

-->

```
具体效果如下：


![](http://upload-images.jianshu.io/upload_images/2141706-9f0136d09ef9ebc0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这里科普一下，因为JE吧专注于ACG口琴演奏，而半音阶口琴的音色是最适合ACG乐曲的，所以这里的谱默认都是半音阶口琴谱，也就是c调，数字谱。关于【】,（）, # 等符号请参考[使用说明](https://github.com/zytx121/justice_eternal/blob/master/instruction.md) 。


## PC端的建立

接着，我就开始着手pc端的展示网页改造（完全是以[BGAIssueBlog]([http://www.bingoogolapple.cn](http://www.bingoogolapple.cn/))为模板，因为之前完全没有自己独立做过vue网站）。一开始只是换了仓库名，改动了一下侧边栏，修改了一下element-ui的主题色。通过阅读这个项目的代码，学习了用axios调用GitHub接口：

```

/*
github API的调用
 */

module.exports = {
  getLabels (vue) {
    return vue.$http.get(`https://api.github.com/repos/${vue.$store.getters.context}/labels`)
  },
  getGitHubUser (vue) {
    return vue.$http.get(`https://api.github.com/users/${vue.$store.getters.gitHubUsername}`)
  },
  getUserInfo (vue) {
    return vue.$http.all([this.getGitHubUser(vue), this.getLabels(vue)])
  },
  getIssues (vue, data) {
    let label = ''
    if (data.label && data.label.trim().length > 0) {
      label = `+label:${data.label}`
    }

    return vue.$http.get(`https://api.github.com/search/issues?q=${data.keyword}+state:open+repo:${vue.$store.getters.context}${label}&sort=created&order=desc&page=${data.currentPage}&per_page=${data.pageSize}`)
  },
  getIssue (vue, number) {
    return vue.$http.get(`https://api.github.com/repos/${vue.$store.getters.context}/issues/${number}`)
  },
  getComments (vue, url) {
    return vue.$http.get(url)
  },
  getReadme (vue) {
    return vue.$http.get(`https://raw.githubusercontent.com/${vue.$store.getters.context}/master/README.md`)
  },
  getInstruction (vue) {
    return vue.$http.get(`https://raw.githubusercontent.com/${vue.$store.getters.context}/master/instruction.md`)
  },
  getRepos (vue, data) {
    return vue.$http.get(`https://api.github.com/users/${vue.$store.getters.gitHubUsername}/repos?sort=stargazers_count&order=desc&page=1&per_page=100`)
  }
}
```
用`marked.js`渲染markdown文件，`highlight.js`代码高亮,`github-markdown-css`将渲染后的markdown设置成github的样式。

利用vuex储存label状态，在各个组件中获取和改变其属性。后来依葫芦画瓢，利用vuex和正则表达式添加了label的部分展示/隐藏功能。
```
const SET_LABELS = 'SET_LABELS'
const SET_ACTIVE_LABEL = 'SET_ACTIVE_LABEL'
const SET_SHOWLABELS = 'SET_SHOWLABELS'

const state = {
  labels: [],
  activeLabel: null,
  showLabels: true,
}

const mutations = {
  [SET_LABELS] (state, labels) {
    state.labels = labels
  },
  [SET_SHOWLABELS] (state, showLabels) {
    state.showLabels = !state.showLabels
  },
  [SET_ACTIVE_LABEL] (state, label) {
    if ((state.activeLabel && label && label.name === state.activeLabel.name) || (!state.activeLabel && !label)) {
      return
    }

    state.activeLabel = label
  }
}

const actions = {
  setLabels: makeAction(SET_LABELS),
  setShowLabels: makeAction(SET_SHOWLABELS),
  updateActiveLabel: makeAction(SET_ACTIVE_LABEL),
}

const getters = {
  labels: (state) => {
    return state.labels
  },
  labels1: (state) => {
    return state.labels.filter(label => label.name.match(/^[A-Z]$/))
  },
  showLabels: (state) => {
    return state.showLabels
  },
  activeLabel: (state) => {
    return state.activeLabel
  }
}

export default {
  state,
  mutations,
  getters,
  actions
}

```

到这里，基础的改造工作就结束了。已经能够正常显示曲谱了（默认只显示按首字母分类的标签）


![](http://upload-images.jianshu.io/upload_images/2141706-1d0c5b4f290c5194.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](http://upload-images.jianshu.io/upload_images/2141706-ac74eded339d0e43.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

目前谱曲库库存告急，正在紧急搬运中- -！欢迎同道中人来做苦力！ [曲库地址](https://github.com/zytx121/justice_eternal/issues)

可是我觉得光是有这个查曲谱的功能未免太单调。于是就想，能否加入几个别的功能。既然是ACG口琴网站，那么acg元素和口琴当然是少不了的。于是我就着手进行口琴录音播放以及口琴视频播放这两个功能的制作。首先做的是视频部分。说到acg视频，我首先想到的就是b站了。然后我就在GitHub搜有没有b站的API什么的。后来在掘金上看到一篇用Vue和typescript重构aplayer播放器的文章。然后我就点进去看了看，觉得这个音频播放器设计的超级漂亮！接着我顺藤摸瓜，无意间发现了DIYgod大佬。其仓库下有无数动漫相关杰作，如 [aplayer](https://github.com/MoePlayer/APlayer)和[dplayer](https://github.com/MoePlayer/DPlayer)。天啦，这正是我想要的！对了，之前那个`ISSUE_TEMPLATE.md`文件也是DIYgod大佬教我设置的！感谢！

接着参照doc，我新建了一个页面，然后引入了DPlayer播放器，值得一提的是该播放器是支持弹幕播放以及弹幕发送的哟！

```
video: {
          url: 'https://api.prprpr.me/dplayer/video/bilibili?aid=1845743',
          pic: 'http://upload-images.jianshu.io/upload_images/2141706-0be35df51011b7b8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240'
        },
        danmaku: {
          id: 'zy00000001',
          api: 'https://api.prprpr.me/dplayer/',
          addition: ['https://api.prprpr.me/dplayer/bilibili?aid=1845743']
        }
```
其中`danmaku.id`字段是指向DIYgod自己的弹幕后端[DPlayer-backend](https://github.com/MoePlayer/DPlayer-backend)里面的弹幕数据，每个视频的这个需要独一无二（doc里面有个列表），不然会和别人存的弹幕车祸。而`danmaku.addition`则是指向b站的弹幕数据，可以读取指定aid视频的弹幕，并显示出来。最后显示在你屏幕前的弹幕是由两部分组成的，而你发送的弹幕会存在[DPlayer-backend](https://github.com/MoePlayer/DPlayer-backend)里面。


![](http://upload-images.jianshu.io/upload_images/2141706-b769f29beeb0d935.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

最后我又同理，在侧边栏加入了aplayer，自动播放口琴演奏的宫崎骏动漫组曲！其实纠结了好久好不要用narrow模式- -！PC端大功告成！
>技术栈：vue + vue-router + vuex + axios  全家桶，以及element-ui

## 移动端的建立

将PC端公布在贴吧之后，由于感受到了贴吧小伙伴们的热情！由于很多吧友都希望能够在手机上使用本网站，而原本的pc端博客不能很好的相应移动端。本着服务群众的想法，我又开始了移动端的开发。本想一步到位做个响应式网站，也找了个响应式 material design ui ，但无奈自己完全没有类似经验，从ui开始实现对我来说话费的时间可能会很长。本着学习的目的，于是我就去找了个移动端的轮子来改造。尝试了一把百度的lavas，把文档通读了一遍，界面什么都很钟意。但是因为默认使用PWA的service worker ，没办法使用github-pages生成。以省钱为第一要务的我，果断放弃。接着我又找到了github上面的一个项目 [Vue.js仿哔哩哔哩动画移动端](https://github.com/youhonglian/Vue-bilibili) 。并以此为基础，开始了网站的改造。期间请教了作者许多问题，都得到很好的解决，所以在这里必须感谢一下[youhonglian](https://github.com/youhonglian)！

#### 录音播放部分

在PC端原有的曲谱查询和视频播放上，我又用aplayer添加了一个页面专门播放大佬们的口琴录音。

![](http://upload-images.jianshu.io/upload_images/2141706-f0d51918b720cf8f.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 视频部分

在视频播放页面上出现了一些问题。。。关于**跨域**

由于原来的项目的部分接口使用的是b站的，本地开发的时候设置了代理，所以能够正常使用。但是部署在github上面后，问题出现了。根据MDN文档[HTTP访问控制（CORS）](https://link.zhihu.com/?target=https%3A//developer.mozilla.org/zh-CN/docs/Web/HTTP/Access_control_CORS)导致跨域并非不一定是浏览器限制了发起跨站请求，而也可能是跨站请求可以正常发起，但是返回结果被浏览器拦截了。通过查看开发者面板中的Network，发现请求确实发出去了，但是没有回应。于是我就蒙蔽了，之前PC端为什么没有出现这种情况？难道DIYgaod提供的API没有跨域吗？接着我恶补了一下关于跨域的相关知识，做了如下总结。

首先，本地开发的时候。实际上，vue生成的静态页面是在express服务器上运行。当静态页面发出get请求后，express服务器能够监听到，去相应的的域名拿到数据并返回给静态页面。
当我们把静态页面上传到服务器后，其实可以把服务器看成我们的电脑。由于浏览器禁止一个域名（我们的网站）的 JS ，在未经允许的情况下读取另一个域名（例如：b站api）的内容（这也是为什么我们要跨域的原因）。所以当静态页面提出一个请求后，我们需要设置服务器，让他去api服务器拿到数据，然后转交给我们的静态页面（也就是反向代理）。其实就是开发环境express服务器做的事！  

- github-pages只能渲染静态页面，而静态页面里面的js代码没办法获取到b站api的内容（跨域）
- 正向代理隐藏真实客户端，反向代理隐藏真实服务端
- 跨域解决方案之一：jsonp，然而axios不支持jsonp。另外，jsonp不能发post请求，不管是否跨域，只要用jsonp方式就只能是get，因为本质是script方式加载的。
-  设置vue-cli模板里面config中的proxyTable后，可以解决开发环境的跨域问题。
- 目前主流解决办法：让后端的同事设置header（详情参考：[HTTP访问控制（CORS）](https://link.zhihu.com/?target=https%3A//developer.mozilla.org/zh-CN/docs/Web/HTTP/Access_control_CORS)）

由于手机无法使用dplayer的弹幕功能，所以我直接使用了video标签播放视频，使用的是 [journey-ad](https://github.com/journey-ad)的**[api](https://github.com/journey-ad/api.imjad.cn)**。我将关于api跨域的疑问告诉了journey-ad，终于解决了这个问题。原来他在所有公开的api的响应头都加了`Access-Control-Allow-Origin: *`字段，所以可以被任何网页发起调用。


回去又读了一遍MDN文档：
```
Access-Control-Allow-Origin: * 
表示所有域名都能访问该资源
Access-Control-Allow-Origin: lightmoon.pw
表示除了lightmoon.pw，其它外域均不能访问该资源
```

![](http://upload-images.jianshu.io/upload_images/2141706-657826c6ad89b732.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

看来之所以访问b站api跨域是因为它没有对所有人开放，而对于dplayer和imjad这类api是对所有人开放的，所以设置了`Access-Control-Allow-Origin: * `响应头，解决了跨域问题。而对于开发环境下的跨域，全都可以通过设置服务器代理来解决。但是对于生产环境下无法配置服务器的（比如github），便无法访问那些不对外开放的api了。

但是这类开放的b站api视频都只能通过电脑播放，在手机上都播放不了。最后我只好用最笨的方法，通过下载对应的视频上传到七牛云生成链接解决。不过视频的相关标签和评论还是调用的api的数据。（在此向观众老爷提问：有什么更好的解决办法吗？）


![](http://upload-images.jianshu.io/upload_images/2141706-29995768c9448ebf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](http://upload-images.jianshu.io/upload_images/2141706-e662416878182504.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 谱曲库部分

将pc段的代码整合了进来。( 注意：移动端项目中使用了vue-axios插件，而PC段是没有使用的，所以作为一个处女座，必须注意axios代码写法的统一) 然后，稍微改了下label的样式，以及内容的布局。


![](http://upload-images.jianshu.io/upload_images/2141706-354c5203576fc93d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![](http://upload-images.jianshu.io/upload_images/2141706-cf68b63b4876e9ea.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](http://upload-images.jianshu.io/upload_images/2141706-48f80fa9ac8f09f7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

最后又改了下sidebar和header。
![](http://upload-images.jianshu.io/upload_images/2141706-35971ac3f6507a55.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

>技术栈：vue + vue-router + vuex + axios  全家桶，以及mint-ui

**完结撒花！！！**

很开心已经有github上面的ACG粉开始义务上传曲谱了！作者自己也会抽空上传曲谱。希望有更多热爱ACG和乐器的程序员大佬加入我们。目前的曲谱的主要来源是moeje.org之前整理的谱曲，以及贴吧中的谱楼。

通过这此网页的改写让我知道了自己的不足，也学到了不少以前完全没有涉及的知识，得到了许多大佬的指点。果然如同阴明大佬所说：抱着一种解决问题的态度去学习知识是最有效率的。连续三天没日没夜的撸代码，终于把自己脑海中的东西基本实现了，也加深了对vue的理解。虽然这次网站改写并不复杂，但也暴露出了我的很多问题，看来接下来自己还需要先在基础知识方面多多努力，好好啃一啃高程和CSS权威指南。

## 关于本站

本站完全出于兴趣构建，基本零成本，如果大家喜欢，还请在github上star一下本项目，顺便follow一下本人~~阿里嘎多！

另外，由于本人能力有限，难免有不尽人意的地方，如果对本站有什么建议也一定！务必！要在issue中提出来哦！阿里嘎多！

最后放上相关地址

移动端网址：[https://justice-eternal.github.io/](https://justice-eternal.github.io/)
PC端网址：[http://lightmoon.pw](http://lightmoon.pw/)
曲库地址：[https://github.com/zytx121/justice_eternal/issues](https://github.com/zytx121/justice_eternal/issues)
贴吧地址： [Justice_Eternal 口琴吧](http://tieba.baidu.com/f?kw=justice_eternal&fr=home)
搬运谱子的苦力组织： [https://github.com/Justice-Eternal](https://github.com/Justice-Eternal)

最后，欢迎喜欢ACG音乐的大佬入半音阶口琴的坑！

[使用说明](https://github.com/zytx121/justice_eternal/blob/master/instruction.md)  |  [新手入门](https://github.com/Justice-Eternal/justice-eternal.github.io/blob/master/start.md)



![](http://upload-images.jianshu.io/upload_images/2141706-4ba8571ca63467f5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)