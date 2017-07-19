---
title: 如何快速搭建一个有域名且持续集成的hexo博客(2.0版)
date: 2017-07-19 07:20:49
tags:
- hexo
- travis
- github
thumbnail: http://upload-images.jianshu.io/upload_images/2141706-596843ecb86bcd9b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
categories: 编程
---

thumbnail: http://upload-images.jianshu.io/upload_images/2141706-596843ecb86bcd9b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
> **前言：**   由于本人最近在学习vue，想把做出来的网页放到一个有自己域名的网站上来供大家学习交流（装B）。首先考虑的是租用云主机，无奈云主机贵的一逼，千幸万苦终于找到一个便宜点的20块钱一个月的国内主机。结果刚把新鲜买的域名绑定上去，过了一会就无法访问了。一脸懵逼好吗！居然需要备案，百度了一下备案周期差不多要一个月。。。玩毛！咨询了一下，原来所有的国内的主机必须备案才能通过绑定的域名进行访问。怪不得我的github上面的hexo博客域名能够访问，原来因为github用的是国外的主机。。。我以前一直以为只有cn域名才需要备案来着？前端时间全部域名都要备案了，我还特意看了下我的hexo博客（top域名），还能正常访问，然后就导致我一直有这个认知误区。。。

后来通过github上面的gh-pages终于[将vue网页展示了出来并绑定了自己的域名](http://www.jianshu.com/p/7cd484bd6dc1)（重要的是没有备案也没有被封- -）。于是我就开始思考，能否将用于对vue网页进行持续集成的Travis CI 用在hexo博客上，于从而大大减少博客更新的繁琐步骤呢？结果发现真的**大大减少了每次更新博客的命令数量**（感兴趣的同学可以和我之前写的[1.0版](http://www.jianshu.com/p/fee3eef70302)进行对比），而且！！！**hexo博客的安装与迁移过程也得到了最大的简化**，于是就有了这篇文章！


### 1. 安装hexo

> 注： 由于本人的电脑是windows系统，之前一直是用的虚拟机上的linux，觉得多此一举，所以改换了windows上的github客户端。所以本文的下列步骤全都是用windows系统进行的。

在安装hexo之前，请确保你的系统安装了`Git`和`Node.js`，不多做赘述。

用Git Shell输出下列命令，进行hexo脚手架的全局安装
```
npm install hexo-cli -g
```
### 2. 初始化hexo

让我们新建一个hexo文件夹然后用Git Shell cd 到该目录下，然后输入下列命令进行hexo的初始化
```
hexo init 
```

### 3. 创建github仓库

直接在官网操作即可，本人是创建了一个以账号名命名的zytx121.github.io的仓库，因为貌似以前看到说只有以用户名作为仓库名才能展示网页。后来发现是完全是谣言，**你github下面任意一个仓库都可以生成有自己独一无二域名的展示网页**（感兴趣的童鞋可以点击[这篇文章](http://www.jianshu.com/p/7cd484bd6dc1)），并不是说一个github账号下只有一个仓库才能有展示页面，也不是说每个账号的多个展示页面只能有一个统一的域名。

### 3. 将github仓库clone到本地


### 4. 将之前初始化的hexo文件里面的所有东西拷贝到github仓库本地目录下

到这里，hexo博客的准备工作就做的差不多了，下面该轮到[**Travis-CI**](https://www.travis-ci.org)登场了!



### 5. 使用Travis-CI对hexo进行持续集成

#### （1） 用github账号登陆

这样就将github与travis-ci进行了绑定，使其能都读取你github中的仓库信息

#### （2） 开启指定仓库并进行相关设置

![](http://upload-images.jianshu.io/upload_images/2141706-54faddfd500f942e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![](http://upload-images.jianshu.io/upload_images/2141706-4bd104509b3810d9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
Build only if .travis.yml is present：是只有在.travis.yml文件中配置的分支改变了才构建 

Build pushes：当推送完这个分支后开始构建

然后到github的setting页面中完成[Access Token的申请](https://github.com/settings/tokens)，将其作为环境变量GH_TOKEN的值存在这里。

![](http://upload-images.jianshu.io/upload_images/2141706-ff5e2d8ed00e565a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
只需要repo这一项权限即可。

#### （3） 创建travis设置文件


最后，让我们回到仓库本地目录，在该目录下新建一个`.travis.yml`文件

文件内容如下：

```
language: node_js
node_js: stable

# Travis-CI Caching
cache:
  directories:
    - node_modules


# S: Build Lifecycle
install:
  - npm install

before_script:
 # - npm install -g gulp


script:
  - hexo g


after_script:
  - cd ./public
  - git init
  - git config user.name "zytx121"
  - git config user.email "592267829@qq.com"
  - git add .
  - git commit -m "Update docs"
  - git push --force --quiet "https://${GH_TOKEN}@${GH_REF}" master:master
# E: Build LifeCycle

branches:
  only:
    - hexo
env:
 global:
   - GH_REF: github.com/zytx121/zytx121.github.io.git
```

看到这里，我们就会发现travis其实就是一个帮你跑脚本的云主机命令行！

他按照我们指定的脚本顺序执行，先是`install`，再是`before_script`，`script`，最后是`after_script`.

`branches`指定了执行脚本的分支。

全局变量`GH_REF`指定了你的仓库地址。

我们首先用`npm install`在 travis 这台全新的主机上进行相关依赖的安装，这里就不需要重新再安装一遍 hexo 然后进行初始化了。安装完所需依赖之后，我们就可以直接使用 hexo 命令。

然后我们用`hexo g`命令来生成静态文件，生成的静态文件默认会被放在 public 目录下。
 
我们cd到public目录，用`git init`初始化仓库，进行相关信息的设置。

最后，travis-ci会将public目录下的文件全部 push 到你所创建仓库的 master 分支上去。

详细内容可以参考这篇文章 [手把手教你使用Travis CI自动部署你的Hexo博客到Github上](http://blog.csdn.net/woblog/article/details/51319364)

### 6. 将github仓库本地目录pull到**hexo分支**上去

这里我使用的是PC客户端，目录下文件变动会显示，输入Summary备注，点击Commit，然后点右上角的Publish即可。（注意，**我们的博客源代码存放在hexo分支上，hexo生成的静态网页文件存放在master分支**。因为gh-pages的默认分支为master，但其实这是可以设置的。）

![](http://upload-images.jianshu.io/upload_images/2141706-a300bd5bccd13de4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**绑定域名**

如果需要绑定自己的域名，只需要在根目录下的`/source/`文件夹内新建一个`CNAME`文件（需要大写），然后在里面写上你的域名。保存后一起push上去即可

然后，在仓库设置中填入你的域名。
![](http://upload-images.jianshu.io/upload_images/2141706-aafc0d5af5579bb5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


同时在你购买域名的服务器管理控制台中，添加如下2个解析：
```
主机记录：@    记录类型： A    记录值：192.30.252.153     TTL： 10分钟
主机记录：www  记录类型： A    记录值：192.30.252.154     TTL： 10分钟
```
这样就完成了你的域名绑定。

**关于404页面：**

同理，你可以在根目录下的`/source/`文件夹内新建一个`404.html`文件，然后在里面写上`<script type="text/javascript" src="http://www.qq.com/404/search_children.js" charset="utf-8"></script>`并保存。这样，当你访问博客中不存在的页面时，浏览器就会自动跳转到腾讯的公益404页面。



这样就大功告成啦！



### 7. 等待Travis-CI执行脚本


![](http://upload-images.jianshu.io/upload_images/2141706-e84b3b4c9a36ad0d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这样就说明成功了，如果红色则说明不成功。该页面会显示运行的命令行，如果出现错误就会报错。

![](http://upload-images.jianshu.io/upload_images/2141706-d70fb026321c3f2f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


到这里为止，博客的搭建方法就介绍完毕了。之后每次需要更新发布文章的话，只需要重复**第6步**即可。

当你需要在其他电脑上更新博客时，可参照下面的代码：
1. `$ git clone https://github.com/zytx121/zytx121.github.io` //拷贝仓库，在本地生成`zytx121.github.io `文件夹
2. `$ cd zytx121.github.io`  //进入该文件夹根目录
3. `$ npm install `（讲道理其实如果只添加博客文章，不进行hexo操作的话，这步其实可以省略。因为travis会在它的主机上安装依赖，帮你生成静态页面。）

然后，你就可以在这台新电脑上愉快的更新博客辣~\(≧▽≦)/~


### 与1.0版本的对比

- 不需要安装`hexo-deployer-git`插件

- 不需要每次部署博客(`hexo g`）前都在本地生产静态文件（`hexo d`）

- 更换电脑后clone到本地后，只需要`npm install`安装依赖，不需要安装hexo，开箱即用。

- 每次更新博客文章后，你所需要做的只是将改动 push 到 hexo 分支，剩下的事 travis-ci 都会帮你做好。

由于持续集成大大简化了更新hexo博客的步骤，让我又开始恢复了之前因为太麻烦而放弃更新的hexo博客！！！