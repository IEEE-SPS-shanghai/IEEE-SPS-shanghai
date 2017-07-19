---
title: 利用github以及travis-ci展示带自己域名的vue页面
date: 2017-07-19 07:20:49
tags:
- vue
- travis
- github
thumbnail: http://upload-images.jianshu.io/upload_images/2141706-61ea043cdc987fd2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
categories: 编程
---

> **前言：**   由于本人最近在学习vue，想把做出来的网页放到一个有自己域名的网站上来供大家学习交流（装B）。首先考虑的是租用云主机，无奈云主机贵的一逼，千幸万苦终于找到一个便宜点的20块钱一个月的国内主机。结果刚把新鲜买的域名绑定上去，过了一会就无法访问了。一脸懵逼好吗！居然需要备案，百度了一下备案周期差不多要一个月。。。玩毛！咨询了一下，原来所有的国内的主机必须备案才能通过绑定的域名进行访问。怪不得我的github上面的hexo博客域名能够访问，原来因为github用的是国外的主机。。。我以前一直以为只有cn域名才需要备案来着？前端时间全部域名都要备案了，我还特意看了下我的hexo博客（top域名），还能正常访问，然后就导致我一直有这个认知误区。。。

后来通过github上面的gh-pages以及持续集成工具travis-ci终于将vue网页展示了出来并绑定了自己的域名（最最重要的是没有备案也没有被封- -）

下面我用[viko16](https://github.com/viko16)写的**[vue-ghpages-blog](https://github.com/viko16/vue-ghpages-blog)**举例，一步一步实现网页的展示。




#### （1） 用github账号登陆[**Travis-CI**](https://www.travis-ci.org)

这样就将github与travis-ci进行了绑定，使其能都读取你github中的仓库信息

#### （2） 开启指定仓库并进行相关设置

![](http://upload-images.jianshu.io/upload_images/2141706-54faddfd500f942e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![](http://upload-images.jianshu.io/upload_images/2141706-61f264beb7f04754.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
Build only if .travis.yml is present：是只有在.travis.yml文件中配置的分支改变了才构建 

Build pushes：当推送完这个分支后开始构建

然后到github的setting页面中完成[Access Token的申请](https://github.com/settings/tokens)，将其作为环境变量GH_TOKEN的值存在这里。

![](http://upload-images.jianshu.io/upload_images/2141706-ff5e2d8ed00e565a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
只需要repo这一项权限即可。

#### （3） 创建travis设置文件


最后，让我们回到vue项目所在仓库的本地目录，在该目录下新建一个`.travis.yml`文件

文件内容如下：

```
branches:
  only:
    - develop

language: node_js

sudo: false

node_js: stable

cache:
  directories:
    - node_modules

addons:
  apt:
    packages:
      - xvfb

install:
  - export DISPLAY=':99.0'
  - Xvfb :99 -screen 0 1024x768x24 > /dev/null 2>&1 &
  - npm install

before_script:
  - git config --global user.name "zytx121"
  - git config --global user.email "592267829@qq.com"
  - git clone --branch gh-pages https://${GH_REF} dist

script:
  - npm test

after_success:
  - npm run build
  - cd dist
  - echo "lightmoon.pw" > CNAME
  - cp index.html 404.html
  - git add --all .
  - git commit --message "Automatically update from travis-ci"
  - git push --quiet --force  "https://${GH_TOKEN}@${GH_REF}" gh-pages:gh-pages

# Note: you should set Environment Variables here or 'Settings' on travis-ci.org
env:
  global:
    - GH_REF: github.com/zytx121/vue-blog.git
```

看到这里，我们就会发现travis其实就是一个帮你跑脚本的云主机命令行！

他按照我们指定的脚本顺序执行，先是`install`，再是`before_script`，`script`，最后是`after_script`.

`branches`指定了执行脚本的分支。

全局变量`GH_REF`指定了你的仓库地址。

首先用`npm install`在 travis 这台全新的主机上进行相关依赖的安装。

然后，travis-ci生成静态文件，并将dist目录下的文件全部 push 到你所创建仓库的 **gh-pages 分支**上去。（注意：该仓库一共有2个分支，**vue源码存放在develop分支，静态页面文件存放在gh-pages 分支**）

如果有域名需要绑定，可以将域名写入CNAME文件。没有，则将其注释掉。

同时在你购买域名的服务器管理控制台中，添加如下2个解析：
```
主机记录：@    记录类型： A    记录值：192.30.252.153     TTL： 10分钟
主机记录：www  记录类型： A    记录值：192.30.252.154     TTL： 10分钟
```

值得一提的是，**你github下面任意一个仓库都可以生成有自己独一无二域名的展示网页**，并不是说一个github账号下只有一个仓库才能有展示页面，也不是说每个账号的多个展示页面只能有一个统一的域名。我们要做的就是将需要展示的页面分支命名为 gh-pages（随便啥都行），然后在仓库设置中进行如下设置。

![](http://upload-images.jianshu.io/upload_images/2141706-a36ab3342809b8e9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**这样就大功告成啦！**

以后每次更新网页或博客后，只需要push到**develop分支**，剩下的事（包括生成vue静态文件）travis-ci都会帮你搞定！


注：本文所用到的例子**[vue-ghpages-blog](https://github.com/viko16/vue-ghpages-blog)**中的文章全部存放在另一个命名为writting的仓库里面。

![](http://upload-images.jianshu.io/upload_images/2141706-78c3b278e645fa68.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

每次文章更新后，甚至不需要再将vue的源代码push到develop分支。你所需要做的，仅仅是直接在travis-ci中点击**Restartbuild**即可！

![](http://upload-images.jianshu.io/upload_images/2141706-2b3e56482264ceea.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


关于持续集成travis-ci可以参考这篇文章 [手把手教你使用Travis CI自动部署你的Hexo博客到Github上](http://blog.csdn.net/woblog/article/details/51319364)

同时，也欢迎大家阅读我的另一篇文章 [如何快速搭建一个有域名且持续集成的hexo博客(2.0版)](http://www.jianshu.com/p/716e74549859)