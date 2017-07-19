---
title: VueConf  感想与总结
date: 2017-05-20 07:20:49
tags:
- 前端学习
- vue
- conf

categories: 编程
---

第一次参加conf好激动的说。来，我们先放几张照片！！

![合照](http://upload-images.jianshu.io/upload_images/2141706-f12e19142b3c8258.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](http://upload-images.jianshu.io/upload_images/2141706-517b341f2c4301a7.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![](http://upload-images.jianshu.io/upload_images/2141706-bde20212f937fcfc.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![](http://upload-images.jianshu.io/upload_images/2141706-2f9b83c53a58b4d2.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
能把自己的第一次献给Vue的第一次简直棒！


今天一天的会议下来，对于刚刚涉足前端领域的我来说收获颇丰，于是将自己的感悟总结在这里与广大的Vue爱好者以及尤大大的粉丝们分享！

##  Vue 2017 现状与发展

> By 尤雨溪 Evan You  Vue.js作者

### 起源


![vue的起源](http://upload-images.jianshu.io/upload_images/2141706-a0ffe61b3afcaa99.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 2013 年 6 月：First Commit (Seed)
- 2013 年 12 月：第一次将项目名字 Vue
- 2014 年 2 月：第一次公开发布 Hacker News
- 2014 年 11 月：0.11 版本（重写）
- 2015 年 4 月：Laravel 社区作者开始使用并宣传
- 2015 年 10 月：Vue.js 1.0 发布（代号：Evangelion，没想到尤大大也喜欢福音战士！好激动！！）
- 2016 年 10 月：Vue.js 2.0 发布（对代码进行了重写 & 一定的向后兼容）

![K？？](http://upload-images.jianshu.io/upload_images/2141706-4baf032d16eefaeb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

最后对于即将发布的2.4版本，将是以K开头的一部动画，但是尤大大不愿透露更多的细节。


![目前国内vue用户](http://upload-images.jianshu.io/upload_images/2141706-4a455febb3791af8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
好多自己梦寐以求的公司啊！！！


### 定位

> Just a View Layer Library

最早只想解决一些视图层的问题，并没有完全服务于大型业务的功能。但是随着 Vue 的发展开始增加辅助工具，例如 `vue-router, vue-loader, vuex`

> The Progress Framework

![](http://upload-images.jianshu.io/upload_images/2141706-440f91a5407038f2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

不需要完全的全家桶，而是可以渐进式的根据需求一点点增加业务复杂度。这样易于上手，也可以更快的应用在老业务上，比侵入式框架易于上手。

### 现状

- GitHub 超过 53,986 个 Star 数，已经是所有类型项目的历史的 **Top 10**
- 每月 55万+ 次 NPM 下载（不算阿里爸爸 CNPM 镜像,算了就是**月破百万**的节奏XD）
- Chrome DevTool 插件 17.4 万日活
- 314 Contributors
- 社区化的开源产品：`NUXT.js，Quasar Framework（Ionic），Element，iView，Muse-UI，Vux，Vuetify，Vue Material`
- 与阿里合作的 Weex
- Microsoft Build TypeScipt 老大作者 Anders Hejlsberg 在 Demo 中 Vue + VSCode （最佳IDE）
- Google I/O Addy Osmani 介绍 Vue + PWA

### SSR

>  Server-Side Rendering ([ssr.vuejs.org](https://link.juejin.im/?target=https%3A%2F%2Fssr.vuejs.org))

服务器端渲染： 在存在代码分割的情况下，通过分析 Webpack 服务端和客户端的构建信息，自动推导需要在客户端预加载的文件，生成最优的 `<script>`和 `<link re="preload/prefetch">`

SSR 性能进一步优化，通过编译时优化获得 2~8x 性能提升。（后面被阴明吐槽性能还是很差，必须在每一层都做缓存）

SSR + webpack code split 完美支持，代码分割不再局限于路由。

### vue-cli 3.0

- 配置依赖化 + 可组合（更新升级）
- PWA by default
- 一个模版，不同参数（`--ts`, `--sr` ...）
- 更好的测试方案

### 长期展望

- 单文件组件 CSS 改进
- 基于 Proxy 的响应式系统重构
- 不再需要 `Vue.set `或者` this.$set`，直接 `=`
- Lazy Observation，性能优化
- 显示构建响应式对象
- HTML Modules：
- 类似单文件组件的新标准（由 Google 起草中）
- 与 Web Components 的兼容

### 个人感悟

会后才知道，原来尤大大昨天凌晨发高烧，今早还是带病来进行了本届大会的开场主题演讲，在会后还热情地和喜爱Vue的小伙伴们一个个合影，不由得深感敬佩！近距离接触尤大大，发现他特别平易近人，丝毫没有大神的架子。了解到尤大大是86年出生的，13年（也就是27岁）写出了第一版Vue。打算把尤大大作为自己的男神和榜样，希望自己五年后也可以像尤大大一样做出属于自己的东西。（貌似有点不自量力23333，总之要加油！You can make it !!）

附上和尤大大的合照一枚！

![](http://upload-images.jianshu.io/upload_images/2141706-5c420326a6330553.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##  Vue SSR 和API Proxy层深度实践

> By i5ting 桑世龙 狼叔 去哪网前端架构师

Vue本身是前端框架，它目前跟服务器唯一的关联就是SSR，基于Stream的Bigpipe实现，虽说是旧瓶装新酒，但还是有很多人不了解其中原理。另外对于Vue项目来说，与后端Api对接、（Spa、大首页）等有没有更好的实践呢？后端Api目前也极为混乱，各种语言、各种实现，真的适合前端么？大家辛苦了，狼叔最懂你。 

首先，狼叔分析 Node.js 现状，并且预测了 2017 年趋势。

### 流行趋势
- PWA
- SSR
- API Proxy
- Isomorphic

### Vue SSR 原理

- wepback 插件内置
- BundleRenderer：dev 状态下的 hot-reload 和 source-map support
- streaming/bigpipe：大文件传输
- cache：缓存 lrc-cache 自动集成
- 内置 service-worker：支持 PWA

### API Proxy

![](http://upload-images.jianshu.io/upload_images/2141706-0304baa406bd1393.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- Browser：双向绑定组件化
- Node Proxy：API 代理给前端浏览器使用
- 服务组装：链接后端微服务


![Vue 与 API Proxy 如何完美结合](http://upload-images.jianshu.io/upload_images/2141706-d45e51294de5a752.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### 个人感悟

狼叔还是很有个人魅力的，嗯。对SSR的原理有了一些基本的认识，知道了目前主流的打包工具为webpack 2，正好最近开始学习webpack，看来没有学错哈哈！狼叔还说如果你想晋升，那么最好学学webpack，看来自己需要更加重视webpack的运用以及原理的学习。


##  谈工程化在Vue.js的优雅设计

> By 张耀春 小春 摩拜单车


前端框架的目的：alleviate the amount of copy & pasting you do between projects.

Pick the right tool for the job.

> 工具复杂度是为了处理内在复杂度所做的投资 - 尤雨溪  [《Vue 2.0，渐进式前端解决方案》](http://www.tuicool.com/articles/6nEjAjb)


### vue-cli

官方出品的命令行脚手架工具，支持：

（1）vue init 按照指定模板，在指定目录生成项目结构

 有 3 种模板初始化方式：
1、官方
2、本地
3、线上其他repo

![vue init 原理](http://upload-images.jianshu.io/upload_images/2141706-bdd20985c835f341.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


（2）vue list 列出线上 vuejs-templates repo 支持的模板列表

![目前的官方模板](http://upload-images.jianshu.io/upload_images/2141706-b79b2aacd23a8da4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

其中大家用的最多的是**webpack**

![vue list 原理](http://upload-images.jianshu.io/upload_images/2141706-a71b032142461d90.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


#### create-react-app VS vue-cli

都是基于 webpack 构建。
create-react-app：更多封装在了react-scripts 里面，同时把它加到了初始项目的依赖里面。
vue-cli：更为直接，把脚本模板都直接放到build 文件夹中，开发者更容易修改。

![主流框架脚手架的差异](http://upload-images.jianshu.io/upload_images/2141706-a1ea9664cf8ebfd0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### webpack
> 和 Vue.js 结合最紧密的构建工具

#### 配置分离
采用` webpack-merge` +` webpack.base.conf.js` + `webpack.prod.conf.js`

#### 本地开发

需要 **Express** 和多个中间件：
- ** connect-history-api-fallback：**在开发单页应用时非常有用，它依赖于HTML5 history API，如果设置为true，所有的跳转将指向index.html
-  **webpack-hot-middleware：**热更新，实现修改代码自动刷新浏览器。
-  **http-proxy-middleware：**代理
-  **express.static：**托管静态文件

![dev-server 原理](http://upload-images.jianshu.io/upload_images/2141706-f35e0eab7a2ee834.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### Webpack插件
DefinePlugin：动态的注入一些变量，比如一些版本、环境信息等

 friendly-errors-webpack-plugin：recognizes certain classes of webpackerrors and cleans, aggregates and prioritizes them to provide a betterDeveloper Experience.

webpack-sftp-client：开发过程中把本地资源 push 到开发机

html-webpack-inline-source-plugin ：html-webpack-plugin 的第三方扩展插件，通过增加一个 {inlineSource: 'regex string'} 选项来内联你的静态文件到 html 中。


![html-webpack-inline-source-plugin 原理](http://upload-images.jianshu.io/upload_images/2141706-9dc575d8c21ea660.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### Vue 组件编译


![vue-component-compiler 原理](http://upload-images.jianshu.io/upload_images/2141706-861e032ef65f9bf2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![vue-component-compiler 原理](http://upload-images.jianshu.io/upload_images/2141706-e7b12393983eb5f1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### vue-loader
Webpack 的插件，处理 ` .vue` 文件中的三部分：
```
*、 template
*、 script
*、 styles
```
![vue-loader 原理](http://upload-images.jianshu.io/upload_images/2141706-f7ce6f6e72670bc2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### 个人感悟

小春的演讲诚意满满干货十足，由于讲的太细还有点超时了。由于小春刚刚从滴滴跳槽到了，导致主办方的关于小春的信息还没更新。自己回来之后重新学了一遍PPT，感觉很多vue的原理性的东西，收获不少。

##  掘金Vue.js后端渲染及重构实践

> By 阴明 掘金创始人

### Vue核心文件目录
```
src/
├── api/              # 接入微服务的基础 API
├── App/              # App Root Component
├── asset/            # 静态文件
├── business/         # 业务
├── component/        # 组件
├── const/            # 常量
├── event-bus/        # Event Bus 事件总线，类似 EventEmitter
├── global/           # 通用定义的 directive, mixin 还有绑定到 Vue.prototype 的函数
├── model/            # Model 抽象层
├── repository/       # 仓库，接入 Vuex 中
├── router/           # 路由
├── service/          # 服务
├── state/            # Vuex 状态管理
├── style/            # 样式
├── util/             # 通用 utility functions
├── view/             # 各个页面
├── client-entry.js   # 前端业务 & build
├── server-entry.js   # SSR业务 & build
├── ...
└── main.js           # Vue Object Initiation
```
```
基础设施层
api/
util/
```
```
领域层 Domain
service/       % 各个 Domain 下的基础功能业务
repository/    %某一个独立 Domain 下的获取数据的业务
model/         %数据抽象层
```
```
业务层
business/        % 各个 Domain 下的具体业务，会引用 service 和 repository 中定义的功能
validator/       %不同数据的 validation 过程
```
```
表现层
state/
router/
component/
view/            % Vue 下具体的交互展示层业务
```

### Event Bus
类似于 Node 中的 EventEmitter
通过事件管理和监听处理异常、Alert、Scroll 触发等



### 404
**需求：**
不通过跳转 URL 来显示 Not Found
 
**解决方案：**
- 我们在路由表的最后配置了 404 路由，如果当前 URL 没有匹配前面的任意一条规则
- Vuex 状态树中有专门的 error module 存储异常
- ​​然后 dispatch 一个 action 设定为 404 展示

### SSR的应用

**需求：**
后端渲染解决性能问题
 
**解决方案：**
- 多层缓存
- 数据层缓存
- 组件层缓存 lru-cache
- 页面层缓存 redis

### 数据一致性
**需求：**
前后端渲染数据一致性问题
 
**解决方案：**
通过某种事件广播机制实现数据的最终一致性
Vuex 本身就有事件广播模型，我们定义了 3 个 mutation 类型：
- ENTITY_CREATED - 实体已创建
- ENTITY_UPDATED - 实体已更新
- ENTITY_DELETED - 实体已删除

###完全通过事件传递行为

略

###情怀部分

> 我相信每一个新技术的出现的最终目的是创造价值
如果一个技术真的好
我就会推荐它，宣传它，帮助它普及给更多的开发者
[用开放的心态去尝试、学习、接受新事物](http://ming.today/)
这即是我做掘金的态度，也是我做技术的态度


### 个人感悟
阴明说这真的是他最后一次技术分享了，不知道大家信不信？我觉得阴明的这次演讲还是很不错的，既有干货又有情怀。在回答问题阶段，阴明说他不是为了学前端而学的前端，他最开始学习的目的单纯只是做自己的个人主页来装逼，因为想要给自己的主页加上炫酷的效果，所以开始自学相关的知识。他认为，抱着一种解决问题的态度去学习知识是最有效率的。我十分认同。以后在自己学习前端的过程中，也要注意问题导向，项目驱动。自己给自己定个目标，例如做出自己的App，小程序。然后让目标驱使自己去主动地获取知识。（与此同时，也要注意扎实的基础知识的掌握。）



 

##  Vue 在饿了么的应用

> By 李清伟 Element 核心开发

- [PWA 在饿了么的实践经验](https://zhuanlan.zhihu.com/p/25800461)






### 个人感悟
element  仅仅只有3个人负责，却能保持至少一周一次更新，佩服！



##  当Weex遇上Vue.js 2.0

> By 马天翼（早弦） 阿里巴巴前端开发工程师、Weex 核心开发

### Weex 1.0
![Weex 1.0 流程图](http://upload-images.jianshu.io/upload_images/2141706-fdd50f439d2e18db.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![与Native通信](http://upload-images.jianshu.io/upload_images/2141706-73a593184ef9064e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![任务中心 流程](http://upload-images.jianshu.io/upload_images/2141706-a0cca9ea09c535ce.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![Paste_Image.png](http://upload-images.jianshu.io/upload_images/2141706-b364aec85b8b5e6c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### Weex 2.0

![weex 2.0 流程图](http://upload-images.jianshu.io/upload_images/2141706-9b8e3e7242ab4196.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


#### 与 web 版本 vue 2.0 的差异点
● DOM
● BOM
● Layout
● scoped
● scroll
● background-image
● 适配问题

#### DOM & BOM
● 不支持 DOM 操作
● 仅支持部分事件类型
● 不支持事件冒泡
● 没有 window、 document、screen、history、location、navigator 等对象

解决办法：

● MVVM 大法好！
● 未来会有更多
● 新版本已经支持
● 使用 weex.config 或者内置模块


#### Flexbox
● Weex 官方指定布局系统
● 规范明确
● 布局适用大部分情况
● 面向未来

#### 其他差异
● 样式作用域默认是 scoped ，即只在当前组件生效
● 只有 scroller 组件默认有滚动效果
● 不能设置背景图
● 与 Native 原生组件共存的适配问题

#### 内存差异
● web 时代，内存能吃吗？
● weex 时代，内存**够**吃吗？


![内存关系](http://upload-images.jianshu.io/upload_images/2141706-989add9558101b42.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这三部分内存属于包含关系。例如：可能一个原生App只泄露了100M的jsfm内存，但是它可能泄露了150M的jscore内存，以及200M的native内存

### 个人感悟
知道了整个weex 项目原来只有13个人(其中前端仅仅3个人)，很吃惊。Weex包含了vue2.0内核，可以看作vue的三端实现。觉得自己可以尝试用weex完成移动端的vue编写。



##  用Vue，vuex构建超大Web应用——IDE

> By 王骆菲  VIDE（原DebugGap）作者

**“某种东⻄的产⽣是由于社会的进步和发展到达⼀定的状态,出现了相应的条件,由此⽽产⽣”**


![vuex](http://upload-images.jianshu.io/upload_images/2141706-afd729fa10dee030.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

对于协同开发而言，只关心有哪些状态可用，不关心具体实现逻辑。

![](http://upload-images.jianshu.io/upload_images/2141706-96cb2a36f2ba9bdd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![](http://upload-images.jianshu.io/upload_images/2141706-94e4bf5a7ca2d735.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![](http://upload-images.jianshu.io/upload_images/2141706-eefe14426b70866b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![](http://upload-images.jianshu.io/upload_images/2141706-4c18d2627bdf4349.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![](http://upload-images.jianshu.io/upload_images/2141706-e853e150a9559b9c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![](http://upload-images.jianshu.io/upload_images/2141706-0c11159f9a8a5127.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

 #### plugin开发
只需要简单的三步，大大降低了编写插件的门槛，从此国人也可以轻松编写自己的插件。
- 导入组件
![](http://upload-images.jianshu.io/upload_images/2141706-fa219538eac2cf37.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 添加视图
![](http://upload-images.jianshu.io/upload_images/2141706-64c8627913e4c4c0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 添加处理类
![](http://upload-images.jianshu.io/upload_images/2141706-f08542d63450561a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### vide的未来规划
1. 未来优先支持vue/weex开发
2. 再支持微信小程序等
3. 基于简单快速的插件开发，服务更多的开发者


### 个人感悟
想尝试写Vue插件


## 结语

充实而愉快的一天就这样结束了，感谢各位大大的带来的精彩内容！（照惯例放上各位大大的合照2333）
![](http://upload-images.jianshu.io/upload_images/2141706-c1b9e144fbfa70d1.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
希望自己能够为vue社区这个大家庭做出自己的贡献，也希望有朝一日能够成为vue在github上的Contributors！！！加油！！！





### 后记

脑洞大开的vue爱好者。。。

![](http://upload-images.jianshu.io/upload_images/2141706-696a9661ca87a585.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![微信图片_20170520223744.jpg](http://upload-images.jianshu.io/upload_images/2141706-03feea228bb8a123.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![微信图片_20170520223747.jpg](http://upload-images.jianshu.io/upload_images/2141706-56991acc66eb3b6f.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![微信图片_20170520223750.jpg](http://upload-images.jianshu.io/upload_images/2141706-1c91735bc7cd94cc.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![微信图片_20170520223753.jpg](http://upload-images.jianshu.io/upload_images/2141706-f67a4327edec6fb9.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![微信图片_20170520223758.jpg](http://upload-images.jianshu.io/upload_images/2141706-a32ce98dd15a8251.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![微信图片_20170520223802.jpg](http://upload-images.jianshu.io/upload_images/2141706-ff4f1f63a7faeaa0.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![微信图片_20170520223804.jpg](http://upload-images.jianshu.io/upload_images/2141706-9ede24a749cb827a.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![微信图片_20170520223949.jpg](http://upload-images.jianshu.io/upload_images/2141706-d50a23612883a5dd.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



部分ppt还没有上传，未完待续~