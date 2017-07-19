---
title: 【微信小程序】——电影详情页面分享设置
date: 2017-04-08 07:20:49
tags:
- 微信小程序


categories: 编程
---

>本文程序是在慕课网七月老师的微信小程序课程基础上自己进行改动。

- 首先js文件中的Page中的data里定义了movie对象，里面存有电影相关信息。
![data](http://upload-images.jianshu.io/upload_images/2141706-1cdfb835e1c3bd99.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![movie对象](http://upload-images.jianshu.io/upload_images/2141706-08b9ee8116fcc893.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 在官方文档中查得分享函数onShareAppMessage


![onShareAppMessage函数](http://upload-images.jianshu.io/upload_images/2141706-2aa2cfe5ce7fe0fb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![字段说明](http://upload-images.jianshu.io/upload_images/2141706-e8c146bb64be9347.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


示例代码如下：
```
onShareAppMessage: function () {
    return {
      title: '自定义分享标题',
      path: '/page/user?id=123',
      success: function(res) {
        // 分享成功
      },
      fail: function(res) {
        // 分享失败
      }
    }
  }
```


由于电影详情页面onLoad时会接受一个参数options（页面跳转所带来的参数），然后我们通过这个options中的id属性再去获取movieId信息，并生成特定电影详情页面的url。最后通过getMovieData函数去向API请求数据。

![获取参数](http://upload-images.jianshu.io/upload_images/2141706-52977d7aabaa7361.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

所以，在onShareAppMessage函数中的title以及path字段需要根据页面跳转所带来的参数而改变，绝不是固定不变的。

由于我们在参数传进来之后将其存在了data.movie中，所以我们此处可以从里面获取我们所需要的this.data.movie.movieid以及this.data.movie.title，并将其存在变量中movieid和title中。
```
  onShareAppMessage: function () {
    var title = this.data.movie.title;
    var movieid = this.data.movie.movieid;
    return {
      title: title,
      path: '/pages/movies/movie-detail/movie-detail?id=' + movieid,
    }
  }
```

这样，我们就完成了电影详情页面的分享功能~~此处应有掌声！！！