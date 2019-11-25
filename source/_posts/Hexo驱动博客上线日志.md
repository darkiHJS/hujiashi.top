---
title: Hexo驱动博客上线日志
date: 2019-11-25 14:27:40
tags:
---
_苦大仇深的Hexo_

### 坑1 无法修改pages的指向
不得不说，目前为止纠结最大一个坑，也是网上错误最多的一个坑。
github的首页已经不能修改pages指向的branch了，强制使用master作为目录。我在反复尝试各种方法后，在没找到如何修改Travis CI上传的目录（默认是gh-pages分支),改用hexo depley自行上传，太麻烦了，失去了我用hexo的意义。

下面是正确的流程
```
  新建一个 repository。如果你希望你的站点能通过 <你的 GitHub 用户名>.github.io 域名访问，你的 repository 应该直接命名为 <你的 GitHub 用户名>.github.io。
```
这边官方文档让你创建 `<你的 GitHub 用户名>.github.io`命名的repository，现在第一步不要这么做，不然你会发现
![图片.png](http://ww1.sinaimg.cn/large/893e6980gy1g9ab2l820zj20pw0e8wih.jpg)
这玩意它不能改！！然后github pages又不能解析你master分支的代码，那不就萎了吗。
所以第一步不能用这个取名法，那就用自己申请的域名做项目名称，比如我就`hujiashi.top`

然后pages的branch就可以可以改了。但是访问路径是 `<username>.github.io/hujiashi.top/`
下面这么做，在你的hexo目录下的`source`中新建`CNAME`文件内容是
```
  你的域名
```
![eee.png](http://ww1.sinaimg.cn/large/893e6980gy1g9abaj27p3j207g05hjra.jpg)

接下来复制你的`<username>.github.io/`或者在命令行中`ping <username>.github.io`拿到ip地址去你的域名网站解析，具体网上教程很多，用github域名时使用CNAME模式就行了

接着如同文档所示的走就可以了。

### 坑2 Tracis CI一直显示missing GH_TOKEN
解决方法：晾了它一天，自己就好了 （？？？）

### 坑3 通过git clone方式安装的nxet主题不起作用
解决方法：按照git提示命令把他纳入自己的库中

