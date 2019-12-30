---
title: Hexo-切换一个主题
date: 2019-12-26 14:55:04
tags: ["博客搭建","快速搭建博客","tags创建"]
categories: ["教程-博客搭建"]
---
[TOC]
## Hexo提升篇-切换一个主题
### 第一轮测试-页面局部显示
疑npm install 导致显示不全，测试二不安装依赖
```
//挑选主题
https://hexo.io/themes/
//克隆主题到本地,放置thmemes
bennyrhys>git clone https://github.com/theme-next/hexo-theme-next.git 
//更改配置文件
theme: hexo-theme-next
//安装依赖插件
$ cd hexo-theme-next
$ npm install
```
### 第二轮测试-全部显示（未安装依赖，切换主题风格）
<!-- more -->
疑配置文件未打开。
* 在 Hexo 中有两份主要的配置文件，其名称都是 _config.yml。 
* 其中，一份位于站点根目录下，主要包含 Hexo 本身的配置；另一份位于主题目录下，这份配置由主题作者提供，主要用于配置主题相关的选项。
* 为了描述方便，在以下说明中，将前者称为站点配置文件， 后者称为主题配置文件。
* 以下所有终端执行的命令都在你的Hexo根目录下
#### 主题配置文件-菜单
我们刚开始默认的菜单只有首页和归档两个，不能够满足我们的要求，所以需要添加菜单，打开 主题配置文件 找到Menu Settings
```
menu:
  home: / || home                          //首页
  archives: /archives/ || archive          //归档
  categories: /categories/ || th           //分类
  tags: /tags/ || tags                     //标签
  about: /about/ || user                   //关于
  #schedule: /schedule/ || calendar        //日程表
  #sitemap: /sitemap.xml || sitemap        //站点地图
  #commonweal: /404/ || heartbeat          //公益404
```
看看你需要哪个菜单就把哪个取消注释打开就行了；
关于后面的格式，以archives: /archives/ || archive为例：
|| 之前的/archives/表示标题“归档”，关于标题的格式可以去themes/next/languages/zh-Hans.yml中参考或修改
||之后的archive表示图标，可以去Font Awesome中查看或修改，Next主题所有的图标都来自Font Awesome。
#### Next主题还有4种风格
我们百里挑一选择了Next主题，不过Next主题还有4种风格供我们选择，打开 主题配置文件 找到Scheme Settings
```
# Schemes
#scheme: Muse
#scheme: Mist
#scheme: Pisces
scheme: Gemini
```
4种风格大同小异，本人用的是[Gemini](https://bennyrhys.github.io)风格，你们可以选择自己喜欢的风格。
#### 侧栏设置
侧栏设置包括：侧栏位置、侧栏显示与否、文章间距、返回顶部按钮等等
打开 主题配置文件 找到sidebar字段
```
sidebar:
# Sidebar Position - 侧栏位置（只对Pisces | Gemini两种风格有效）
  position: left        //靠左放置
  #position: right      //靠右放置

# Sidebar Display - 侧栏显示时机（只对Muse | Mist两种风格有效）
  #display: post        //默认行为，在文章页面（拥有目录列表）时显示
  display: always       //在所有页面中都显示
  #display: hide        //在所有页面中都隐藏（可以手动展开）
  #display: remove      //完全移除

  offset: 12            //文章间距（只对Pisces | Gemini两种风格有效）

  b2t: false            //返回顶部按钮（只对Pisces | Gemini两种风格有效）

  scrollpercent: true   //返回顶部按钮的百分比
```
#### 头像设置
打开 主题配置文件 找到Sidebar Avatar字段
```
# Sidebar Avatar
avatar: /images/header.jpg
```
这是头像的路径，只需把你的头像命名为header.jpg（随便命名）放入themes/next/source/images中，将avatar的路径名改成你的头像名就OK啦！

//最新方法-配置
```
# Sidebar Avatar
avatar:
  # Replace the default image and set the url here.
  url: /images/head_logo.jpg
  # If true, the avatar will be dispalyed in circle.
  rounded: true
  # If true, the avatar will be rotated with the cursor.
  rotated: true

# Posts / Categories / Tags in sidebar.
site_state: true
```
#### 标签
```
//命令创建
hexo new page "tags" 
//修改创建的文件
---
title: 标签
date: 2019-12-26 19:23:43
type: "tags"
---
//打开主题的tag
//给文章加个标签

```
#### 分类
```
//命令创建
hexo new page "categories"
//修改新生成的文件
---
title: 分类
date: 2019-12-26 19:37:01
type: "categories"
---
//打开categories 

```

#### 媒体外链
//配置文件
social:
  GitHub: https://github.com/bennyrhys || github
  E-Mail: mailto:bennyrhys@163.com || envelope
  QQ: 2389992466 || qq
  WeiChat: bennyrhys-sir || weixin
  CSDN: https://blog.csdn.net/weixin_43469680 || fa-link
//修改图标
图标网站：[点击访问](http://www.fontawesome.com.cn/)

#### 关于
```
//创建
hexo new page "about" 
//配置文件
//启用
```
#### 相册
```
//命令创建
hexo new page "photos"
//第三方github工具
justified-gallery
```
#### 阅读量
//打开配置busuanzi
```
busuanzi_count:
  enable:true
```
\themes\next\layout_third-party\下的busuanzi.swing
将
src=“https://dn-lbstatics.qbox.me/busuanzi/2.3/busuanzi.pure.mini.js”
修改为
src=“https://busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js”
#### 添加动态背景
js文件放在\themes\next\source\js\src
更新\themes\next\layout\_layout.swig文件，在末尾（在前面引用会出现找不到的bug）添加以下 js 引入代码：
```
<script type="text/javascript" src="/js/src/back.js" ></script>

//法二
配置文件，不太靠谱
canvas_nest:
  enable: false
```
#### gitalk评论
gitalk：一个基于 Github Issue 和 Preact 开发的评论插件
详情Demo可见：https://gitalk.github.io/
在GitHub上注册新应用，链接：https://github.com/settings/applications/new
参数说明：
Application name： # 应用名称，随意
Homepage URL： # 网站URL，如https://asdfv1929.github.io
Application description # 描述，随意
Authorization callback URL：# 网站URL，https://asdfv1929.github.io

点击注册后，页面跳转如下，其中Client ID和Client Secret在后面的配置中需要用到，到时复制粘贴即可：
Client ID
-52515de43eada8e083b
Client Secret
-ee2994d96e2d4a5684188df17a49fe8e9a6c3d6
gitalk.swig
新建/layout/_third-party/comments/gitalk.swig文件，并添加内容：
#### valine评论
//注册LeanCloud
注册地址 https://leancloud.cn/
获取key，添加安全，网站链接
配置文件valine对应id


#### 头像圆形旋转
介绍一下实现头像圆形，鼠标经过旋转或者一直让旋转效果，主要是修改 Hexo 目录下 \themes\next\source\css\_common\components\sidebar\sidebar-author.styl 文件。
修改 sidebar-author.styl 文件中 .site-author-image CSS 样式如下：
```
.site-author-image {
  display: block;
  margin: 0 auto;
  padding: $site-author-image-padding;
  max-width: $site-author-image-width;
  height: $site-author-image-height;
  border: $site-author-image-border-width solid $site-author-image-border-color;
  
/* 头像圆形 */
  border-radius: 80px;
  -webkit-border-radius: 80px;
  -moz-border-radius: 80px;
  box-shadow: inset 0 -1px 0 #333sf;

  /* 鼠标经过头像旋转360度 */
  -webkit-transition: -webkit-transform 1.5s ease-out;
  -moz-transition: -moz-transform 1.5s ease-out;
  transition: transform 1.5s ease-out;
}

img:hover {
  /* 鼠标经过头像旋转360度 */
  -webkit-transform: rotateZ(360deg);
  -moz-transform: rotateZ(360deg);
  transform: rotateZ(360deg);
}

```
#### 阅读进度条
reading_progress:
  enable: true

#### 百度推送
//配置文件
baidu_push: true

#### 优化SEO

更改网站副标题（将是主要网站描述）和所有文章/页面标题的标题层次结构，以便更好地

seo: true //建议 true

#### 搜索
npm install hexo-generator-searchdb --save
#### 友链
```
# Blog rolls
links_settings:
  icon: link
  title: 友链
  # Available values: block | inline
  layout: block

links:
  #Title: http://yoursite.com
  吉他易学网/EasyGuitar: https://www.996cloud.work
```
#### 开启打赏
```
reward_settings:
  # If true, reward will be displayed in every article by default.
  enable: true
  animation: true
  comment: 请作者喝杯茶～

reward:
  wechatpay: /images/wechatpay.png
  alipay: /images/alipay.jpg
  #bitcoin: /images/bitcoin.jpg

```
#### 开启订阅公众号 
有些版本在，wechat属性配置，升级版没有
#### 阅读更多
老版本auto_excer属性配置高度
新版替代法
<!-- more -->//夹在文章中
#### 分享
配置文件jiathis：true
已经淘汰
#### 加载效果
```
pace:
  enable: true
  # Themes list:
  # big-counter | bounce | barber-shop | center-atom | center-circle | center-radar | center-simple
  # corner-indicator | fill-left | flat-top | flash | loading-bar | mac-osx | material | minimal
  theme: minimal
```
#### 字数统计，阅读时长


#### 标题toc优化
```
toc:
  enable: true
  # Automatically add list number to toc.
  number: true
  # If true, all words will placed on next lines if header width longer then sidebar width.
  wrap: true
  # If true, all level of TOC in a post will be displayed, rather than the activated part of it.
  expand_all: true
  # Maximum heading depth of generated toc.
  max_depth: 6
```
#### 图片不显示问题
//设置站点配置文件
post_asset_folder: true
//下载插件