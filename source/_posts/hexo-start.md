layout: '[layout]'
title: 如何搭建一个拥有自己域名的hexo博客网站
date: 2016-05-27 09:12:52
tags: [干货]
categories: 编程
---

作为[Hexo博客](https://github.com/hexojs/hexo)入门新手，你有没有遇到好不容易搭好的网站，因为手残不小心将虚拟机还原，导致几天的努力功亏一篑呢？你是否因为不知道如何备份hexo网站文件和换了一台电脑而无法更新博客而苦恼？
不要担心！跑者小越今天就把如何只用一个github仓库建立一个绑定自己域名的同时可以远程备份的hexo网站的小技巧统统告诉你！

<!--more-->
1. 初始化git本地仓库
```
$ git init
```

2. 关联远程库
```
$ git remote add origin https://github.com/zytx121/zytx121.github.io.git
```

3. 将远程库同步至本地
```
$ git pull origin master
```

4. 新建hexo分支，并切换到hexo分支
```
$ git checkout -b hexo
```

5. 将hexo分支关联到远程库
```
$ git push origin hexo
```

6. 安装hexo
```
$ npm install -g hexo-cli
```

7. 初始化hexo
```
$ hexo init
$ npm install
$ npm install hexo-deployer-git --save
```

8. 修改_config,.yml中的deploy参数（将hexo生成的静态网页保存到master分支）
```
deploy:
  type: git
  repository: https://github.com/zytx121/zytx121.github.io.git
  branch: master
```

9. 安装主题（以next示范）
```
$ git clone https://github.com/iissnan/hexo-theme-next themes/next
```

10. 启用主题
```
修改_config,.yml中的**theme**参数为 theme: next
```

11. 生成文章(可在**source/_posts/**目录下用markdown格式编辑刚生成的**post-name.md**)
```
$ hexo new [layout] "post-name"
```

12. 生成静态网页
```
$ hexo g
```

13. 在本地服务器测试生成的网页`http://localhost:port （port 预设为 4000，可在 _config.yml 设定）`
```
$ hexo s
```

14. 将生成的网页部署至服务器
```
$ hexo d
```

15. 最后，将配置好的网站系统文件提交至远程库的hexo分支（建议先用`$ git branch`确保处于hexo分支）
```
$ git add -A
$ git commit -m"1.0" //引号中内容为提交备注，可任意填写，但不能为空
$ git push origin hexo
```

大功告成！！

***
到这里为止，博客的搭建方法就介绍完毕了。之后每次需要更新发布文章的话，只需要**重复11~15步**即可。

当你需要在其他电脑上更新博客时，可参照下面的代码：
1. `$ git clone https://github.com/zytx121/zytx121.github.io.git` //拷贝仓库，在本地生成`zytx121.github.io.git `文件夹
2. `$ cd zytx121.github.io.git`  //进入该文件夹根目录
3. `$ npm install hexo`
4. `$ npm install` //注意：与之前不同的是，这里不需要`hexo init`命令
5. `$ npm install hexo-deployer-git --save`
然后，你就可以在这台新电脑上愉快的更新博客辣~\(≧▽≦)/~

当需要hexo发布更新时，你可以使用`$ npm update hexo`命令更新

在安装hexo之前，请确保你的系统安装了`Git`和`Node.js`
```
可参考下列命令：
$ sudo apt-get install git-core //安装Git
$ curl https://raw.github.com/creationix/nvm/master/install.sh | sh //安装Node.js

```

如果需要绑定自己的域名，只需要在根目录下的`/source/`文件夹内新建一个`CNAME`文件（需要大写），然后在里面写上你的域名。同时在你购买域名的服务器管理控制台中，添加如下2个解析：
```
主机记录：@    记录类型： A    记录值：192.30.252.153     TTL： 10分钟
主机记录：www  记录类型： A    记录值：192.30.252.154     TTL： 10分钟
```
保存即可。这样就完成了你的域名绑定，赶快尝试输入你的域名访问博客吧！

关于404页面：
你可以在根目录下的`/source/`文件夹内新建一个`404.html`文件，然后在里面写上`<script type="text/javascript" src="http://www.qq.com/404/search_children.js" charset="utf-8"></script>`并保存。这样，当你访问博客中不存在的页面时，浏览器就会自动跳转到腾讯的公益404页面。

***

注意：
>创建的仓库名称务必与你的github账号同名，这样才能生成github首页网站

>该仓库有`master`和`hexo`2个分支，`master`分支用来存放静态网页文件，`hexo`用来存放hexo网站系统文件

>本教程要求掌握基本的shell命令行语句，可参考：[快乐的 Linux 命令行](http://billie66.github.io/TLCL/)

>博客文章建议采用markdown格式，如果您不是很了解可以看这篇文章：[怎样引导新手使用 Markdown？](https://www.zhihu.com/question/20409634)



**感谢阅读～**

