小程序项目结构
=======

一.了解项目的基本组成结构
-------------

1.  pages用来存放所有小程序的页面
2.  utils用来存放工具性质的模块(例如：格式化时间的自定义模块)
3.  app.js小程序项目的入口文件
4.  app.json小程序项目的全局配置文件
5.  app.wxss小程序项目的全局样式文件
6.  project.config.js项目的配置文件
7.  sitemap.json用来配置小程序及其页面是否允许被微信索引

二.小程序页面的组成部分
------------

小程序官方建议，把`所有小程序的页面都存放在pages目录`中，以单独的文件夹存在：  
![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0d0c2831d4ce44d7ba3a7cc3927f49cd~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

其中，每个页面由4个基本文件组成，它们分别是：

1.  .js文件(页面的脚本文件，存放页面的数据，事件处理函数等)
2.  .json文件(当前页面的配置文件，配置窗口的外观、表现等)
3.  .wxml文件(页面的模版结构)
4.  .wxss文件(当前页面的样式表文件)

三.json配置文件
----------

json配置文件的作用：json是一种数据格式，在实际开发中，json总是以配置文件的形式出现。小程序中通过不同的`.json配置文件`，可以对小程序项目`进行不同级别的配置。`

小程序项目中有4种json配置文件，分别是：

*   项目根目录中的app.json配置文件
*   项目根目录中的project.config.json配置文件
*   项目根目录中的sitemap.json配置文件
*   每个页面文件夹中的.json配置文件

### 1.app.json

app.js是当前小程序的全局配置，包括了小程序的所有页面路径、窗口外观、界面表现、底部tab等。  
![截屏2022-09-22 下午8.39.26.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/883516c0269c48cdb567cae434eade28~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?) navigationBarBackgroundColor：导航栏背景颜色，如 `#000000`，`#666`，十六进制颜色 navigationBarTextStyle：导航栏标题颜色，仅支持 `black` / `white`

> **修改项目首页：调整app.json中pages数组中页面路径的前后顺序，即可修改项目的首页。小程序会把排在第一位的页面当做项目首页进行渲染。**

`在app.json文件中的"pages"属性中，直接写"pages/my/my"，然后保存，项目会自动创建my文件夹`

### 2.project.config.json

project.config.json是项目配置文件，用来记录小程序开发工具所做的个性化配置，例如：

*   setting中保存了编译相关的配置
*   projetname中保存的是项目名称
*   appid中保存的是小程序的账号ID

### 3.sitemap.json

![截屏2022-09-22 下午8.47.17.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/2a761efc9a0a4d0ab8e4f051cd68ceb5~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 4.每个页面文件夹中的.json配置文件

小程序中的每一个页面，可以使用.json文件来对本页面的窗口外观进行配置，页面中的配置项会覆盖app.json的window种相同的配置项。

四.WXML模版
--------

### 1.wxml 和 html的区别

（1）标签名称不同

*   html（div、span、img、a）
*   wxml（view、text、image、navigator）

（2）属性节点不同

`<a href="#">超链接</a>`

`<navigator url="/pages/index/index"></navigator>`

（3）提供了类似于vue中的模板语法

*   数据绑定
*   列表渲染
*   条件渲染

### 2.wxss 和 css的区别

![](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0f86a927bc10476e8c886c4aa4991d93~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

wxss还有： @import样式导入

五.小程序中js文件分类
------------

![截屏2022-09-22 下午9.26.30.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/93178de0c93143a280f504f88cd87885~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

小程序宿主环境
=======

宿主环境包括 通信模型、运行机制、组件、API

1.通信模型
------

小程序通信的主体是渲染层和逻辑层。

![](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8f52665f156f45b38ded74ee37979255~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

2.运行机制
------

小程序启动的过程：  
![](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c1b5c0d0c79c440da5aa16c6c3efc618~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

页面渲染的过程：  
![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/33ed47008ad9451781414cca72d64704~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

3.组件
----

小程序中组件的分类：网址如下 [developers.weixin.qq.com/miniprogram…](https://link.juejin.cn?target=https%3A%2F%2Fdevelopers.weixin.qq.com%2Fminiprogram%2Fdev%2Fcomponent%2F "https://developers.weixin.qq.com/miniprogram/dev/component/")

### 常用的**视图容器**类组件

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/50b99af79b7b47e59556e72ed37065a5~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)  
**swiper和swiper-item组件的基本使用:** ![微信图片_20221023202037.jpg](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ebae752d052f4036be2136e5474267a0~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

**swpier组件的常用属性：** ![微信图片_20221023202037.jpg](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8d0ffb57adaa44bcb9e11b7273303e4c~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 常用的**基础内容**组件

![](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e27751d60c9d4e36ae2bcbe8831ea271~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

> 长按复制的话：要在text标签中添加selectable属性  
> `<text user-select="true">文本组件text</text>`  
> rich-text富文本可以添加nodes属性：  
> `<rich-text nodes="<h3 style='color:pink;'>富文本框</h3>"></rich-text>`

### 其他常用组件

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/eb053c4c78874e8cb22fb6e954cca7f8~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

![截屏2022-09-23 下午9.55.49.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9004a91d106c4a91b13e7eb154855e7b~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

4.API
-----

小程序API的3大分类：

![截屏2022-09-23 下午10.00.26.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/342685d7ca4347c386b7b76d6f35e2e6~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

正式开始学习小程序开发内容
=============

一、wxml模板语法
----------

### 1.数据绑定

基本原则： 在data中定义数据，在wxml中使用数据。

动态绑定的时候和vue不同【vue中是在src前加：，且imgSrc不加{{ }}】。但在小程序中无论是内容还是属性都要加{{ }}

js

复制代码

`//页面结构 <image src="{{imageSrc}}" mode="widthFix"></image> //页面数据 Page({   data: {     imageSrc:'xxx'   }, })`

### 2.事件绑定

#### （1）小程序中常用的事件：

![截屏2022-09-24 下午5.21.12.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/591e39f641f9499ea74ff91711fe462d~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### （2）事件对象的属性列表：

![截屏2022-09-24 下午5.24.28.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/40bfe16a80c748379693d394dd2b6230~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

taeget 和 currentTarget的区别： ![截屏2022-09-24 下午5.28.40.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6f5dad77a3064af8a960590015647831~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### （3）bindtap的语法格式：

在小程序之中，不存在html中的onclick鼠标点击事件，而是通过**tap事件**来响应用户的触摸行为。

js

复制代码

`// 通过bindtap，为组件绑定 tap 触摸事件 <button type="primary" bindtap="changCount">按钮</button> // 在js文件中定义函数，事件参数通过形参 event(一般写成e)来接收 Page({   changCount(e){      console.log(e); //事件参数对象 e   }, })`

#### （4）在事件处理函数中为data中的数据赋值：

通过调用 this.setData(dataObject)方法。

js

复制代码

`Page({   data: {     count:1   },   // 修改count的值   changCount(){     this.setData({       count:this.data.count+1     })   }, })`

#### （5）事件传参：

小程序中的事件传参比较特殊，`不能在绑定事件的同时为事件处理函数传递参数。`

js

复制代码

`// 错误写法 <button type="primary" bindtap="tapHandle(123)">事件传参</button> //小程序会把bindtap的属性值，统一当成事件名称来处理， //相当于事件名为 tapHandle(123)。`

解决办法：可以为组件提供 **dada-**\* 自定义属性传参，其中 \* 代表的是参数的名字。

js

复制代码

`<button type="primary" bindtap="tapHandle" data-info="{{24}}">事件传参</button> // info会被解析为参数的名字 // 数值 24 会被解析为参数的值 // 如果不加 {{}} 传过去的就是字符串了`

在事件处理函数中，通过 **event.target.dataset.参数名** 即可获取到具体参数的值。

js

复制代码

 `tapHandle(e){     //dataset是一个对象，包含了所有通过 data-* 传递过来的参数项     console.log(e.target.dataset);     //通过 dataset 可以访问到具体参数的值     console.log(e.target.dataset.info);   },`

#### （6）bindinput的语法格式：

在小程序中，通过input事件来响应文本框的输入事件，语法格式如下：

js

复制代码

`<input bindinput="inputHandler"/> inputHandler(e){     // e.detail.value 是变化过后，文本框最新的值     console.log(e.detail.value);          //实现文本框和data之间的数据同步     this.setData({         msg: e.detail.value     }) },`

### 3.条件渲染

如果要一次性控制多个组件的展示与隐藏，可以使用一个`<block></block>`标签将多个组件包装起来，并在`<block>`标签上使用`wx:if`控制属性。

注意：`<block>`并不是一个组件，它只是一个包裹性质的容器，不会在页面中做任何渲染

在小程序中，直接使用 `hidden="{{ true/false}}"` 也能控制元素的显示与隐藏。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/39ce9dfd7c4f493a815e2d2fb60eca02~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 4.列表渲染

通过wx:for可以根据指定的数组，循环渲染重复的组件结构，语法如下：

js

复制代码

`//默认情况下，当前循环项的索引用index表示；当前循环项用item表示 <view wx:for="{{array1}}">索引是{{index}}--数组项是{{item}}</view>`

手动指定索引和当前项的变量名：

*   使用wx:for-index指定索引名 (写key的时候不加大括号)
*   使用wx:for-item指定循环项的变量名

js

复制代码

`<view wx:for="{{array1}}" wx:for-index='id' wx:for-item='arr'>索引是{{id}}--数组项是{{arr}}</view>`

wx:key的使用：类似于vue列表渲染中的:key,小程序在实现列表渲染时，也建议为渲染出来的列表项指定唯一的key值，从而提高渲染的效率。

#### 案例一：轮播图案例

js

复制代码

`<view>     <swiper>         <swiper-item wx:for="{{imageslist}}" wx:key="id">             <image src="{{item.image}}" alt=""/>             <!-- <text>{{index}}</text> -->    输出为 0             <!-- <text>{{item.id}}</text> -->  输出为 1         </swiper-item>     </swiper> </view> // data数据 imageslist:[       {id:1,image:"http://xxx3.jpg"},       {id:2,image:"http://xxx4.jpg"},       {id:3,image:"http://xxx5.jpg"} ] // wxss样式 swiper{   height: 350rpx; } swiper image{   width: 100%;   height: 100%; }`

#### 案例二：经典九宫格

js

复制代码

`<view class="grid-list">     // 与案例四相关联，传递当前点击格子的id和name     <navigator url="/pages/shoplist/shoplist?id={{item.id}}&title={{item.name}}" open-type="navigate" class="grid-item" wx:for="{{catelist}}" wx:key="id">       <image src="{{item.icon}}"></image>       <text>{{item.name}}</text>     </navigator> </view> // 样式 .grid-list{     display: flex;     flex-wrap: wrap;     border-top: 1px solid #efefef;     border-left: 1px solid #efefef; } .grid-item{     width: 33.33%;     height: 200rpx;     display: flex;     flex-direction: column;     justify-content: center;     align-items: center;     border-right: 1px solid #efefef;     border-bottom: 1px solid #efefef;     box-sizing: border-box; } .grid-item image{     width: 60rpx;     height: 60rpx; } .grid-item  text{     font-size: 24rpx;     margin-top: 10rpx; }`

![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4bcc16b12e1546c0873e5de37f4d5fab~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

二、wxml模板样式
----------

### 1.rpx

rpx是微信小程序独有的，用来解决屏适配的尺寸单位。

实现原理：rpx把所有设备的屏幕，在宽度上等分为750份(即：当前屏幕的总宽度为750rpx)。

小程序在不同设备上运行的时候，会自动把rpx的样式单位换算成对应的像素单位来渲染，从而实现屏幕适配。

三、全局配置
------

### 1.全局配置文件及常用的配置项

![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/211bb06c865c4c15b78ab2677f3cbc9f~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 2.全局配置-window

小程序窗口的组成部分：  
![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/306a1382266d41af92074c14a3b99bc2~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

window节点常用的配置项： ![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/762cae3b24a84312ad1b4ea14a1af8cd~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

上拉触底是指手指在屏幕上的上拉滑动操作，从而加载更多数据的行为。【具体是指进度条距离底部的距离为50px的时候加载更多数据】

### 3.全局配置-tabBar

#### 1.什么是tabBar

![截屏2022-09-24 下午10.21.18.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f7fd887c500442279ecbbb387c2f62f5~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### 2.tabBar的6个组成部分

![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4312efda2664454c9a31ced6f0592596~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### 3.tabBar节点的配置项

![截屏2022-09-24 下午10.29.06.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/397498b492ed4b2a88b8c5c716555cbd~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### 4.每个tab项的配置选项

![截屏2022-09-24 下午10.30.16.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4f211e7332ea4888ac5ae48629247edc~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### 5.配置tabBar

![](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6881330eb30441bb81deb07095483845~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?) ![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c97cb90cdd0c4b33a04e2d878826d0c0~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?) ![](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/abfa7d623652468a91cf59694c5b19d7~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

js

复制代码

 `"tabBar":{     "list":[         {             "pagePath":"pages/index/index",             "text":"首页"         },         {             "pagePath":"pages/my/my",             "text":"我的"         }     ] } ,`

四、页面配置
------

app.json中的window节点，可以全局配置小程序中每个页面的窗口表现。

如果某些小程序页面想要有特殊的窗口表现，此时，“页面级别的 .json配置文件”就可以实现这种需求。

当页面配置与全局配置冲突时，根据就近原则，最终的效果以页面配置为准。

页面配置中常用的配置项：

![截屏2022-09-24 下午10.41.07.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d68c4b8c2ae74d399f7f8f892a13747b~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?) `不建议在全局配置中设置enablePullDownRefresh属性，建议在单独的页面json文件中设置。` 注意在真机演示的时候需要手动关闭。

五、网络数据请求
--------

### 1.小程序中网络数据请求的限制

出于安全性方面的考虑，小程序官方对数据接口的请求做出了如下两个限制：

（1）只能请求https类型的接口  
（2）必须将接口的域名添加到信任列表中

### 2.配置request合法域名

需求：假设在自己的微信小程序中，希望请求 [www.escook.cn/](https://link.juejin.cn?target=https%3A%2F%2Fwww.escook.cn%2F "https://www.escook.cn/") 域名下的接口

配置步骤：登录微信小程序管理后台->开发->开发设置->服务器域名->修改request合法域名 ![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d210c0d983fe47cab2ac4a0254a7f839~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 3.如何跳过request合法域名校验

![截屏2022-09-25 下午2.15.20.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ccdb9693086247c3ab7636477d9149f3~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 4.发起 GET 请求

调用微信小程序提供的`wx.request()方法，可以发起get数据请求`，示例代码如下：

js

复制代码

 `getHandle(){     wx.request({       //请求的接口必须基于https协议       url: 'https://www.escook.cn/api/get',       method:'GET',       data:{         name:'tom',         age:24       },       //请求成功后的回调函数       success:(res)=>{          console.log(res.data.data);       }     })   },`

### 5.发起 POST 请求

调用微信小程序提供的`wx.request()方法，可以发起post数据请求`，示例代码如下：

js

复制代码

 `postHandle(){     wx.request({       //请求的接口必须基于https协议       url: 'https://www.escook.cn/api/post',       method:'POST',       data:{         name:'tom',         age:24       },       //请求成功后的回调函数       success:(res)=>{          console.log(res.data.data);       }     })   },`

### 6.在页面刚加载时请求数据

在很多情况下，我们需要在页面刚加载的时候，自动请求一些初始化的数据，此时需要在页面的**onLoad**事件中调用获取数据的函数，示例如下：

js

复制代码

   `/**    * 生命周期函数--监听页面加载    */   onLoad(options) {     this.getHandle();     this.postHandle()   },`

### 7.关于跨域和Ajax的说明

跨域问题只存在于基于浏览器的web开发中。由于小程序的宿主环境是微信客户端，所以小程序中**不存在跨域**的问题。

Ajax技术的核心是依赖于浏览器中的XMLHttpRequest这个对象，由于小程序的宿主环境是微信客户端，所以小程序中不能叫做“发起Ajax请求”，而是叫做“**发起网络数据请求**”。

六、页面导航
------

小程序中实现页面导航的两种方式

（1）声明式导航

*   在页面上声明一个`<navigator>`导航组件
*   通过点击`<navigator>`组件实现页面跳转

（2）编程式导航

*   调用小程序的导航API，实现页面的跳转

### 1.声明式导航-导航到tabBar页面

tabBar页面指的是被配置为tabBar的页面。  
在使用`<navigator>`组件跳转到指定的tabBar页面时，需要指定`url`属性和`open-type`属性，其中

*   url表示要跳转的页面的地址，必须以 / 开头
*   open-type表示跳转的方式，必须为switchTab

js

复制代码

 `<navigator url="/pages/message/message" open-type="switchTab">跳转到tabBar页面</navigator>`

### 2.声明式导航-导航到非tabBar页面

非tabBar页面指的是未被配置为tabBar的页面。  
在使用`<navigator>`组件跳转到指定的tabBar页面时，需要指定`url`属性和`open-type`属性，其中：

*   url表示要跳转的页面的地址，必须以 / 开头
*   open-type表示跳转的方式，必须为navigate

js

复制代码

 `<navigator url="/pages/message/message" open-type="navigate">跳转到非tabBar页面</navigator>`

为了简便，在导航到非tabBar页面时，open-type属性可省略。

### 3.声明式导航-后退导航

如果要后退到上一页面或多级页面，则需要指定open-type属性和delta属性，其中：

*   open-type的值必须是navigateBack，表示要进行后退导航
*   delta的值必须是数字，表示要后退的层级。

为了简便，如果只是后退到上一层，则可以省略delta，因为默认值就是1。

js

复制代码

`// 我测试不管用？？ 后退不了是怎么回事？？ //我现在在message页面，是tabBar配置页面 <navigator open-type="navigateBack">后退到home页面</navigator>`

我测试不管用？？ 后退不了是怎么回事？？

原因：`tabBar 页面是不能实现后退的效果的`. 因为, 当我们跳转到 tabBar 页面，会关闭其他所有非tabBar 页面,所以当处于 tabBar 页面时, 无页面可退。

解决办法：用路径url跳转过去，参考1、2条笔记。

### 4.编程式导航-导航到tabBar页面

调用wx.switchTab(Object object)方法，可以跳转到tabBar页面。其中Object参数对象的属性列表如下： ![](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1f46b20daf4f44069d386a9289bc54b6~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

js

复制代码

`//页面结构 <button bindtap='gotoMessage'>跳转到消息页面</button> //编程式导航，跳转到tabBar页  gotoMessage(){       wx.switchTab({         url:'/pages/message/message'       })  }`

### 5.编程式导航-导航到非tabBar页面

js

复制代码

`//页面结构 <button bindtap='gotoInfo'>跳转到消息页面</button> //编程式导航，跳转到tabBar页  gotoInfo(){       wx.navigateTo({         url:'/pages/info/info'       })  }`

### 6.编程式导航-后退导航

![截屏2022-09-25 下午5.23.47.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b41f2d507b954a64b69af81abe60bd7c~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 导航传参

#### 1.声明式导航传参

![截屏2022-09-25 下午5.27.04.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/def0730b91dc4d9bbc1e861073e9acd8~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### 2.编程式导航传参

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/2318e0cc934d44819698ed4a1bfddb15~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### 3.接收导航参数---在onLoad中

通过声明式导航传参或编程式导航传参所携带的参数，可以直接在onLoad事件中直接获取到。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/91f352cd9f194e1e9dab0959c54fff3f~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

一般会把传递过来的参数对象赋值给data中的query，因为要用到这个数值。

js

复制代码

`data中定义一个 query:{} //在onload函数中添加 this.setData({      query:options })`

七、页面事件
------

### 1.下拉刷新事件

下拉刷新是移动端的专有名词，指的是通过手指在屏幕上的下拉滑动操作，从而重新加载页面数据的行为。

#### 启动下拉刷新有两种方式：

（a）全局开启下拉刷新

*   在app.json的window节点中，将enablePullDownRefresh设置为true

（b）局部开启下拉刷新【为需要的页面单独开启下拉刷新的效果】

*   在页面的.json配置文件中，将enablePullDownRefresh设置为true

#### 配置下拉刷新窗口的样式：

在全局或页面的.json配置文件中，通过backgroundColor和backgroundTextStyle来配置下拉刷新窗口的样式，其中：

*   backgroundColor用来配置下拉刷新窗口的背景颜色，仅支持16进制的颜色值
*   backgroundTextStyle用来配置下拉刷新的loading的样式，仅支持dark和light

#### 监听页面的下拉刷新事件：

在页面的.js文件中，通过`onPullDownRefresh()函数即可监听当前页面的下拉刷新事件`。

![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/97aaeff61ff1426cb866f9cd98cbf77f~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### 停止下拉刷新的效果：

当处理完下拉刷新后，下拉刷新的loading效果会一直显示，所以需要手动隐藏loading效果。此时，调用`wx.stopPullDownRefresh()可以停止当前页面的下拉刷新`。

![截屏2022-10-08 下午9.22.32.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4e4efa2f27874413941d6e9869aa2098~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 2.上拉触底事件

上拉触底是移动端的专有名词，通过手指在屏幕上的上拉滑动操作，从而加载更多数据的行为。

监听页面的下拉触底事件：  
在页面的.js文件中，通过`onReachBottom()函数即可监听当前页面的上拉触底事件`。

配置上拉触底距离：  
`上拉触底距离指的是`触发上拉触底事件时，`滚动条距离页面底部的距离`。  
可以在全局或页面的.json配置文件中，通过`onReachBottomDistance属性来配置上拉触底的距离`。小程序默认的是50px，可按需求修改。

#### 案例三--下拉触底事件添加loading效果和节流处理：

js

复制代码

`//wxml文件代码： // 第 3 步：渲染UI结构并美化页面效果 <view wx:for="{{colorList}}" wx:key="index" class="num-item" style="background-color: rgba({{item}});">{{item}}</view> //js文件代码： Page({     data: {         colorList:[],         //第 6 步：对上拉触底进行节流处理         /* 6.1 在data中定义isloading节流阀---false 表示当前没有进行任何数据请求---true 表示当前正在进行数据请求*/         isloading:false     },     //第 1 步：定义随机获取颜色的方法并存储数据     getColors(){         /* 6.2 在getColor()方法中修改isloading节流阀的值---在刚调用方法时将节流阀设置为true---在complete回调函数中，将节流阀重置为false*/         this.setData({          isloading:true         })         //  第 5 步：（5.1）添加loading提示效果         wx.showLoading({           title: '数据加载中...',         })         wx.request({           url: 'https://www.escook.cn/api/color',           method:'GET',           // 将返回数据中的data项重命名为res           success:({data:res})=>{   //解构data属性             this.setData({               colorList:[...this.data.colorList,...res.data] //将旧数据与新数据进行拼接             })           },           //（5.2）.隐藏loading效果，无论请求成功或失败都要关闭加载框           complete:()=>{             wx.hideLoading()             // 6.3 请求结束后，把状态改回来             this.setData({               isloading:false             })           }         })     },     onLoad(options) {         //第 2 步：在页面一加载的时候就调用方法获取colorlist         this.getColors();     },     onReachBottom() {         /* 6.4 判断节流阀的值，从而对数据请求进行节流控制---如果节流阀的值为true，则阻止当前请求---如果节流阀的值为false，则发起数据请求*/         if(this.isloading) return         //第 4 步：在上拉触底时调用获取随机颜色的方法         this.getColors()     }, }) //wxss文件代码`

效果图：  
![](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e3bbf6fd01d8449c9090b411864b0161~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

扩展：自定义编译模式，可以改变首次要运行的页面。 ![](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1f2a58738b9b44a9b3c82486f672c6e1~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

八、生命周期
------

### 1.什么是生命周期

`生命周期`是指一个对象从`创建->运行->销毁`的整个阶段，`强调的是一个时间段`。

也可以把小程序运行的过程概括为生命周期：

*   小程序的`启动`，表示`生命周期的开始`。
*   小程序的`关闭`，表示`生命周期的结束`。
*   中间小程序运行的过程，就是小程序的生命周期。

### 2.生命周期的分类

在小程序中，生命周期分为两类，分别是：

（1）`应用生命周期`

*   特指小程序从启动->运行->销毁的过程

（2）`页面生命周期`

*   特指小程序中，每个页面的加载->渲染->销毁的过程

其中，`页面`的生命周期`范围较小`，`应用程序`的生命周期`范围较大`，如图所示： ![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/90980e8ea1074a1eacfa2d1a3cb9c82d~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 3.什么是生命周期函数

`生命周期函数`：是由小程序框架提供的`内置函数`，会伴随着生命周期，`自动按次序执行`。

`生命周期函数的作用`：允许程序员`在特定的时间点``，执行某些特定的操作`。例如，页面刚加载的时候，可以在onLoad生命周期函数中初始化页面的数据。

注意：`生命周期`强调的是`时间段`，`生命周期函数`强调的是`时间点`。

### 4.生命周期函数的分类

小程序中的生命周期函数分为两类，分别是：

（1）`应用的生命周期函数`

*   特指小程序从启动->运行->销毁期间一次调用的那些函数

（2）`页面的生命周期函数`

*   特指小程序中，每个页面从加载->渲染->销毁期间依次调用的那些函数

### 5.应用的生命周期函数

小程序的`应用周期函数`需要在`app.js`中进行声明，示例如下：

js

复制代码

`// app.js文件 App({   //当小程序初始化完成时，会触发 onLaunch（全局只触发一次）   onLaunch: function () {},   //当小程序启动，或从后台进入前台显示，会触发 onShow   onShow: function (options) {},   //当小程序从前台进入后台，会触发 onHide   onHide: function () {},   } })`

### 6.页面的生命周期函数

小程序的`页面生命周期函数`需要在页面的`.js文件中`进行声明，示例如下：

js

复制代码

`Page({   //生命周期函数--监听页面加载   onLoad(options) {},   //生命周期函数--监听页面初次渲染完成   onReady() {},   //生命周期函数--监听页面显示   onShow() {},   //生命周期函数--监听页面隐藏   onHide() {},   //生命周期函数--监听页面卸载   onUnload() {}, })`

九、WXS脚本
-------

### 1.什么是wxs

wxs是小程序独有的一套脚本语言，结合wxml，可以构建出页面的结构。

### 2.wxs的应用场景

`wxml中无法调用在页面的.js中定义的函数`，但是，wxml中可以调用wxs中定义的函数。因此，小程序中wxs的`典型应用场景`就是“`过滤器`”。

### 3.wxs和javascript的关系

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ca402613bd574e87b36b239e53447ef9~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 4.wxs脚本-基础语法

（1）内嵌 wxs 脚本 wxs代码可以编写在wxml文件中的`<wxs>`标签内，就像javascript代码可以编写在html文件中的`<script>`标签内一样。

wxml文件中的每个`<wxs></wxs>`标签，必须提供`module属性`，用来指定当前wxs的模块名称，方便在wxml中访问模块中的成员。

js

复制代码

`// username:'yqy'    <view>{{ m1.toUpper(username) }}</view>  //页面 YQY <wxs module="m1">     module.exports.toUpper = function(str){         return str.toUpperCase()     } </wxs>`

（2）定义外联的wxs脚本

wxs代码还可以编写在以 `.wxs 为后缀名的文件内`，就像javascript代码可以编写在以 .js为后缀名的文件中一样。

（3）使用外联的 wxs脚本

> module.exports 一个文件只能用一次

在wxml中引入外联的wxs脚本时，必须为`<wxs>`标签添加`module和src属性`，其中：

*   `module`用来指定模块的名称
*   `src`用来指定要引入的脚本的路径，且`必须是相对路径`

js

复制代码

`// username2：'YQY' <view>{{m2.toLower(username2)}}</view> // 页面展示 yqy // 引入文件 <wxs src="../../utils/tools.wxs" module="m2"></wxs> // 这个 .wxs文件写在 utils文件夹下 function toLower(str) {   return str.toLowerCase() } module.exports = {   toLower:toLower //这里要写全，不能简写 }`

### 5.wxs的特点

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e033f05edabb4ade900869ae66c34472~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?) ![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5c8644316ae449e7a318c925c1d2b0c5~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?) ![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5c42bd6a78244a2b88f134c056e0abe6~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?) ![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/cf3e0df3d836494192323772707fb982~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

案例四--点击九宫格中的任意一个格子跳转到新界面并展示相关数据
-------------------------------

1.首先是shoplist.wxml文件的布局

js

复制代码

`<view wx:for="{{shoplist}}" wx:key="id" class="listview">     <view class="img">       <image src="{{ item.images[0] }}" alt=""/>       </view>     <view class="info">       <text>{{item.name}}</text>       <text>手机：{{m1.splitPhone(item.phone) }}</text>       <text>地址：{{item.address}}</text>     </view> </view> // 引入外联的wxs脚本 <wxs src="../../utils/tools.wxs" module="m1"></wxs>`

2.shoplist.json文件--打开下拉刷新设置，并设置样式

js

复制代码

`{   "usingComponents": {},   // 设置下拉触底的距离   "onReachBottomDistance": 200,   // 单独打开当前页面的下拉刷新   "enablePullDownRefresh": true,   "backgroundColor": "#efefef",   "backgroundTextStyle": "dark" }`

3.shoplist.js文件

js

复制代码

``Page({     data: {         query:{},         shoplist:[],         //请求参数         page:1,         pageSize:10,         total:0,         //加载效果         isloading:false     },     //生命周期函数--监听页面加载     onLoad(options) {         // 存储传过来的id和name         this.setData({             query:options         })         this.getShopList()     },     getShopList(callback){          this.setData({             isloading:true         })         // 展示loading效果         wx.showLoading({             title: '加载下一页...',         })         wx.request({             url: `https://www.escook.cn/categories/${this.data.query.id}/shops`,             method:'GET',             //以分页的形式获取商铺列表数据，传递参数             data:{                 _page:this.data.page,                 _limit:this.data.pageSize             },             success:(res)=>{                 this.setData({                 shoplist:[...this.data.shoplist,...res.data],                 //  header是一个对象，里面的X-Total-Count有字符，所以用字符串形式，获得是字符串“80”，所以要转成数值类型                 total:res.header['X-Total-Count'] - 0                 })             },             // 请求完成后关闭loading效果             complete:()=>{                 wx.hideLoading()                 this.setData({                   isloading:false                 })                 callback && callback()             }         })     },     //生命周期函数--监听页面初次渲染完成     onReady() {         wx.setNavigationBarTitle({             title: this.data.query.title         })     },     //页面相关事件处理函数--监听用户下拉动作     onPullDownRefresh() {         // 需要重置关键的数据         this.setData({             page:1,             pageSize:10,             total:0         })         // 重新发起数据请求         this.getShopList(()=>{             //并不是所有的请求都要关闭下拉刷新效果,所以把它作为回调函数传过去比较合适              wx.stopPullDownRefresh()         })     },     //页面上拉触底事件的处理函数     onReachBottom() {         if(this.data.page*this.data.pageSize>=this.data.total){             // 证明没有下一页的数据了             return wx.showToast({                 title: '数据加载完毕',                 icon:'none'             })         }         // 判断是否正在加载数据         if(this.isloading) return         this.setData({             page:this.data.page+1         })         this.getShopList()     }, })``

4.外联的wxs文件

js

复制代码

`// 分隔手机号 function splitPhone(str) {     if(str.length!== 11) return str     // 把一个字符串分割成字符串数组     var arr = str.split('')      // 在第4个位置删除0个元素，添加-     arr.splice(3,0,'-')     arr.splice(8,0,'-')     // 数组元素转换为字符串,json()返回新的字符串     return arr.join('') } module.exports={     splitPhone:splitPhone //这里要写全，不能简写 }`

效果图：  
![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5fd93395b0e5474cbdbe716aec394a37~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

十、自定义组件
-------

### 1.组件的创建与引用

#### （1）创建组件

①在项目的根目录中，鼠标右键，创建 components -> test文件夹(这是一个组件)  
②在新建的components -> test文件夹上，右键“新建component”  
③输入组件名称  
注意：为了保证目录结构的清晰，建议把不同的组件，存放到单独目录中。

#### （2）引用组件

引用方式分为“局部引用”和“全局引用”，顾名思义:

*   局部引用：组件只能在当前被引用的页面内使用
*   全局引用：组件可以在每个小程序页面中使用

#### （3）局部引用组件

在页面的`.json`配置文件中引用组件的方式，叫做"局部引用"。

js

复制代码

`{   // 在.json文件中引入组件   "usingComponents": {     "my-test":"/components/test/test"   } } <!-- 在页面的 .wxml文件中使用组件 --> <my-test></my-test>`

#### （4）全局引用组件

在 `app.json` 全局配置文件中引用组件的方式，叫做"全局引用"。和局部引用组件相同。

#### （5）全局引用VS局部引用

根据组件的**使用频率**和**范围**，来选择合适的引用方式:

*   如果某组件在**多个页面中经常被用到**，建议进行“全局引用”
*   如果某组件只在**特定的页面中被用到**，建议进行“局部引用”

#### （6）组件和页面的区别

从表面来看，组件和页面都是由js、json、wxml和wxss这四个文件组成的。但是，组件和页面的.js与 json文件有明显的不同:

*   组件的json文件中需要声明`"component":true`属性
*   组件的.js文件中调用的是`Component()`函数
*   组件的事件处理函数需要定义到`methods`节点中

js

复制代码

`// json文件 {   "component": true,   "usingComponents": {} }`

js

复制代码

`// js文件 Component({     //组件的属性列表     properties: {},     //组件的初始数据      data: {},     //组件的方法列表     methods: {} })`

### 2.样式

#### （1）组件样式隔离

默认情况下,自定义组件的样式只对当前组件生效,不会影响到组件之外的结构。好处:

*   防止外界的样式影响组件内部的样式
*   防止组件的样式破坏外界的样式

#### （2）组件样式隔离的注意点

*   app.wxss中的全局样式对组件无效
*   只有class 选择器会有样式隔离效果, id 选择器、属性选择器、标签选择器不受样式隔离的影响

建议:在`组件和引用组件`的页面中建议使用class择器,`不要使用id、属性、标签选择器!`

#### （3）修改组件的样式隔离属性

默认情况下,自定义组件的样式隔离特性能够防止组件内外样式互相干扰的问题。但有时,我们希望在外界能够控制组件内部的样式,此时,可以通过`stylelsolation`修改组件的样式隔离选项,用法如下:

js

复制代码

`// 在组件的.js文件中新增如下配置 Component({     options:{         styleIsolation: "apply-shared"     } }) // 或在组件的 .json 文件中新增如下配置 {     "styletsolation":"apply-shared" }`

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/db9a75ec9b5a40e48eb2b173105966bb~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 3.数据、方法和属性

#### （1）data数据

在小程序组件中，`用于组件模板渲染`的`私有数据`，需要定义到`data节点`中。

#### （2）methods方法

在小程序组件中，`事件处理函数`和`自定义方法`需要定义到`methods节点`中。

#### （3）properties属性

在小程序组件中，properties是组件的对外属性，`用来接收外界传递到组件中的数据`。

js

复制代码

`// index.wxml文件：把max传给 test组件 <my-test max="9"></my-test> // properties属性的值也可以用于页面渲染 <view>{{max}}</view> // test.wxml文件 <text>当前count值是：{{count}}</text> <button bindtap="addCount">+1</button> // test.js文件 Component({     properties: {         // 第一种方式：简化的方式         // max:Number         // 第二种方式：完整的定义方式（没有传值的情况下）         max:{             type:Number,             value:10         }     },     data: {         count:0     },     //组件的方法列表【包含事件处理函数和自定义方法】     methods:{         //事件处理函数         addCount(){             if(this.data.count>=this.properties.max) return             this.setData({ count:this.data.count + 1})             //通过 this直接调用自定义方法             this._showCount()          },         //自定义方法建议以 _ 开头         _showCount(){             wx.showToast({                 title:'count值为:' + this.data.count,                 icon:'none'             })         }     } })`

#### （4）data和properties区别

在小程序的组件中，properties属性和data数据的用法相同，它们都是`可读可写`的，只不过：

*   data更倾向于存储组件的私有数据
*   properties更倾向于存储外界传递到组件中的数据

`this.data === this.properties // true`

#### （5）使用 setDate修改properties 的值

由于`data数据和properties属性`在本质上没有任何区别，因此properties属性的值也可以用于页面渲染或使用setData为properties中的属性重新赋值。

### 4.数据监听器

#### （1）什么是数据监听器

数据监听器是用于`监听和响应任何属性和数据字段的变化`，从而执行特定的操作。它的作用类似于vue中的watch侦听器。在小程序组件中，数据监听器的基本语法格式如下：

#### （2）基本用法

js

复制代码

`Component({     //数据监听节点     observers:{         // 前后顺序一致         '字段a,字段b':function (字段a的新值,字段b的新值) {             // do something           }     }, })`

#### （3）监听对象属性的变化

数据监听器支持监听对象中`单个`或`多个属性`的变化

js

复制代码

`Component({     observers:{     '对象.属性A,对象.属性B':function(属使A的新值,属性B的新值){     //触发此监听器的3种情况:     //【为属性A值】使用setData 设置this.data.对象,属性A时触发     //【为属性B值】使用setData 设置this.data.对象,属性B时触发     //【直接为对象赋值】使用setData 设置 this.data.对象时触发     //do something. })`

#### （4）监听对象中指定属性的变化（在下面案例中）

#### 案例五--自定义组件的数据监听器

js

复制代码

``// 引入test2组件 <my-test2></my-test2> // test2.wxml 自定义组件 <view class="colorbox" style="background-color: rgba({{fullColor}});">颜色值：{{fullColor}}</view>     <view class="rgbbox">         <button bindtap="changeR" size="mini" type="default">R</button>         <button bindtap="changeG" size="mini" type="primary">G</button>         <button bindtap="changeB" size="mini" type="warn">B</button>     </view> </view> // test2.js文件 Component({     data: {         rgb:{           r:0,           g:0,           b:0         },         fullColor:'0,0,0'     },     methods: {         changeR(){               this.setData({                 "rgb.r":this.data.rgb.r+5>255?255:this.data.rgb.r+5,                     })         },         changeG(){               this.setData({                 "rgb.g":this.data.rgb.g+5>255?255:this.data.rgb.g+5,                     })         },         changeB(){               this.setData({                 "rgb.b":this.data.rgb.b+5>255?255:this.data.rgb.b+5,                     })         }     },     // 监听对象中指定属性的变化     observers:{         'rgb.r,rgb.g,rgb.b':function (r,g,b) {               this.setData({                  fullColor:`${r},${g},${b}`               })          }     } })``

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/54518cca38534fc5b40166af5ab78ca0~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### （5）监听对象中所有属性的变化

如果某个对象中需要被监听的属性太多,为了方便,可以使用`通配符 **` 来监听对象中`所有属性的变化`。

js

复制代码

``observers:{     'rgb.**':function (obj) {         this.setData({             fullColor:`${obj.r},${obj.g},${obj.b}`         })     } }``

### 5.纯数据字段

#### （1）什么是纯数据字段

纯数据字段指的是那些`不用于界面渲染的data字段`。（案例五中的rgb{}就是纯数据字段）

应用场景：例如有些情况下，某些data中的字段`既不会展示在界面上，也不会传递给其他组件`，仅仅在当前组件内部使用。带有这种特性的data字段适合被设置为纯数据字段。

好处：纯数据字段有助于提升页面更新的性能。

#### （2）使用规则

在Component构造器的options节点中，指定`pureDataPattern`为一个`正则表达式`，字段名符合这个正则表达式的字段将成为纯数据字段。

js

复制代码

`Component({     options:{         //指定所有 _ 开头的数据字段为纯数据字段         pureDataPattern:/^_/     },     data: {         a:true, // 普通数据字段         _b:true // 纯数据字段   }, })`

#### （3）使用纯数据字段改造数据监听器案例

js

复制代码

`Component({     options:{         //指定所有 _ 开头的数据字段为纯数据字段         pureDataPattern:/^_/     },     data: {         // 将所有的 rgb 改为 _rgb         _rgb:{             r:0,             g:0,             b:0     },   }, })`

### 6.组件的生命周期

#### （1）组件`全部的`生命周期函数

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/dcd0d8c052b34774b0c743745b9931fb~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### （2）组件`主要的`生命周期函数

在小程序组件中，最重要的生命周期函数有3个，分别是`created、attached、detached`，它们的特点如下：

1.组件实例`刚被创建好`的时候,created 命周期函数会被触发

*   此时还不能调用 setData
*   通常在这个生命周期函数中,只应该用于给组件的this添加一些自定义的属性字段

2.在组件`完全初始化完毕、进入页面节点树后`,attached 命周期函数会被触发

*   此时,this.data 已被初始化完毕
*   这个生命周期很有用,绝大多数初始化的工作可以在这个时机进行(例如发请求获取初始数据)

3.在组件`离开页面节点树后`,detached 生命周期函数会被触发

*   退出一个页面时,会触发页面内每个自定义组件的detached 生命周期函数
*   此时适合做一些清理性质的工作

#### （3）`lifetimes`节点

在小程序组件中，生命周期函数可以直接定义在Component构造器的第一级参数中，可以在lifetimes字段内进行声明(这是推荐的方式，其优先级最高)。

js

复制代码

`Component({     // 推荐用法     lifetimes:{         attached(){},         detached(){}     },     // 旧式写法     attached(){},     detached(){} })`

### 7.组件所在页面的生命周期

#### （1）什么是组件所在页面的生命周期

有时，`自定义组件的行为依赖于页面状态的变化`，此时就需要用到`组件所在页面的生命周期`。

例如：每当触发页面的show生命周期函数的时候，希望重新生成一个随机的rgb颜色值。在自定义组件中，组件所在页面的生命周期函数有如下3个，分别是： ![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/23d9ae284dae42e287a2bf062e6859b9~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### （2）pageLifetimes节点

组件所在页面的生命周期函数，需要定义在pageLifetimes节点中。

js

复制代码

`// 自定义组件的 .js文件 Component({     pageLifetimes:{            // 组件所在页面被展示时，生成随机颜色值         show:function () {   //页面被展示             this._randomColor()         },          hide:function () {}, // 页面被隐藏         resize:function () {} // 页面尺寸变化     },     methods: {         // 非事件处理函数建议以 _ 开头         _randomColor(){             this.setData({                 _rgb:{                   r:Math.floor(Math.random()*256),                   g:Math.floor(Math.random()*256),                   b:Math.floor(Math.random()*256),                 }             })         }     } })`

### 8.插槽

#### （1）什么是插槽

在自定义组件的wxml结构中，可以提供一个`<slot>`节点(插槽)，`用于承载组件使用者提供的wxml结构`。 ![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8c6df88edfa24a2398f2c9a6166eda44~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### （2）单个插槽

在小程序中，默认每个自定义组件只允许使用一个`<slot>`进行占位，这种个数上的限制叫做单个插槽。

js

复制代码

`<!-- 组件的使用者 --> <my-test3>     <!-- 这部分内容被放置在组件 <slot>的位置上 -->     <view>这是message插入到test组件slot中的内容</view> </my-test3> <!-- 组件的封装者 --> <view>     <text>我是自定义组件的内部节点</text>     <!-- 对于不确定的内容，可以使用<slot>进行占位，具体内容由组件的使用者决定 -->     <slot></slot> </view>`

#### （3）`启用`多个插槽

在小程序的自定义组件中，需要使用多个`<slot>`插槽时，可以在组件的.js文件中，通过以下方式进行启用。

js

复制代码

`Component({     options:{         multipleSlots:true //在组件定义时的选项中启用多 slot 支持     } })`

#### （4）`定义`多个插槽

可以在组件的 .wxml中使用多个`<slot>`标签，以不同的`name`来区分不同的插槽。

js

复制代码

`<my-test3>     <view slot="before">插入到test组件slot name="before"中的内容</view>     <view slot="after">插入到test组件slot name="after"中的内容</view> </my-test3> <!-- 组件的封装者 --> <view>     <slot name="before"></slot>     <slot name="after"></slot> </view>`

### 9.父子组件之间的通信

#### （1）父子组件之间通信的3种方式

① 属性绑定

*   用于父组件向子组件的指定属性设置数据，仅能设置JSON兼容的数据 ② 事件绑定
*   用于组件向父组件传递数据，可以传递任意数据 ③ 获取组件实例
*   父组件还可以通过this.selectComponent()获取子组件实例对象
*   这样就可以直接访问子组件的任意数据和方法

#### （2）属性绑定

属性绑定用于实现`父向子传值`，而且只能传递普通类型的数据，无法将方法传递给子组件。

子组件在`properties`节点中`声明对应的属性`并使用。（示例在下面（3）中）

#### （3）事件绑定

`事件绑定`用于实现`子向父传值`，可以传递任何类型的数据。使用步骤如下：

① 在`父组件`的js中，定义一个函数，这个函数`即将`通过自定义事件的形式，传递给子组件  
② 在`父组件`的wxml中，通过自定义组件的形式，将步骤1中定义的函数引用，传递给子组件  
③ 在`子组件`的js中，通过调用`this.triggerEvent('',{/* 参数对象 */}),`将数据发送到父组件  
④ 在`父组件`的js中，通过`e.detail`获取到子组件传递过来的数据

父组件：

js

复制代码

`<!-- 使用 bind:自定义事件名称(推荐：结构清晰) --> <my-test4 count='{{count}}' bind:addCount='addCount'></my-test4> <!-- 使用 bind 后面直接写上自定义事件名称 --> <!-- <my-test4 count='{{count}}' bindaddCount='addCount'></my-test4> --> Page({     data: {         count:1,     },     addCount(e){;         this.setData({             count:e.detail.value         })     } })`

子组件：

js

复制代码

`<view>父组件传过来的count：{{count}}</view> <button type="primary" bindtap="countadd">count+1</button> Component({     properties: {         count:Number     },     methods: {         countadd(){             this.setData({                 count:this.properties.count+1             })             this.triggerEvent('addCount',{                 value:this.properties.count             })         }     } })`

#### （4）获取组件实例

可在父组件里调用`this.selectComponent`("id或class选择器"),获取子组件的实例对象,从而直接访问子组件的任意数据和方法。调用时需要传入一个`选择器`,例如 this.selectComponent(".my-component")。

js

复制代码

`getChild(){     // 切记下面参数不能传递标签选择器'my-test4',不然返回的是null     const child = this.selectComponent('.child')     child.setData({         count:child.properties.count+1     }) },`

### 10.behaviors

#### （1）什么是behaviors

**相当于组件中的组件**

behaviors是小程序中，`用于实现组件间代码共享`的特性，类似于Vue.js中的“mixins”。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6872ac7359cb43f285c57c137514a375~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### （2）behaviors的工作方式

每个behavior可以包含一组属性、数据、生命周期函数和方法。组件引用它时,它的属性、数据和方法会被合并到组件中。  
每个组件可以引用多个 behavior,behavior 可以引用其它 behavior.

#### （3）创建behavior

调用Behavior(Object object)方法即可创建一个共享的behavior实例对象，供所有的组件使用： ![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/039eff2ed0c94067a04618c963a342c2~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### （4）导入并使用behavior

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1ad3a473accb41cf90e898d4a5b6943b~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### （5）behavior中所有可用的节点

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/863350819620488e84ba9ec8bd27609f~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### （6）同名字段的覆盖和组合规则

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5377a47a431445368475dcd991f03d65~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?) [developers.weixin.qq.com/miniprogram…](https://link.juejin.cn?target=https%3A%2F%2Fdevelopers.weixin.qq.com%2Fminiprogram%2Fdev%2Freference%2Fapi%2FBehavior.html "https://developers.weixin.qq.com/miniprogram/dev/reference/api/Behavior.html")

十一、使用npm包
---------

小程序对npm的支持与限制： ![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/2c1966eed4f14b5c9124d1317a14b9a5~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 1.什么是Vant Weapp

![image.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a756c37505cd4fcd90ff02b755819d04~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?) [youzan.github.io/vant-weapp/…](https://link.juejin.cn?target=https%3A%2F%2Fyouzan.github.io%2Fvant-weapp%2F%23%2Fhome "https://youzan.github.io/vant-weapp/#/home")

### 2.安装Vant组件库

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/10be6b8c2aea444391b82b18c8e8804d~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?) ([youzan.github.io/vant-weapp/…](https://link.juejin.cn?target=https%3A%2F%2Fyouzan.github.io%2Fvant-weapp%2F%23%2F%255Bquickstart "https://youzan.github.io/vant-weapp/#/%5Bquickstart")\])

### 3.使用Vant组件

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8c8ccc748ec349838ac2dd08822fcf65~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 4.定制全局主题样式

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a171c55aa99e4992b921050763afa764~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8b000c6a52fb4f89bb8db7b89f9038a5~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 5.API Promise化

#### （1）基于回调函数的异步API的缺点

默认情况下，小程序官方提供的异步API都是基于回调函数实现的，例如，网络请求的API需要按照如下的方式调用：

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/01da67d8a18146a29adbf4cb8c3c83ee~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### （2）什么是API Promise化

`API Promise化`，指的是`通过额外的配置`，将官方提供的、基于回调函数的异步API，`升级改造为基于Promise的异步API`，从而提高代码的可读性、维护性，避免回调地狱的问题。

#### （3）实现API Promise化

在小程序中,实现API Promise 主要依赖于 `miniprogram-api-promise` 这个第三方的npm包。它的安装和使用步骤如下:

js

复制代码

`npm install --save miniprogram-api-promise@1.0.4`

js

复制代码

`// 在小程序入口文件中(app.js)，只需调用一次 promisifyAll()方法 // 即可实现异步 API 的 Promise化 import { promisifyAll } from 'miniprogram-api-promise' const wxp = wx.p = { } promisifyAll(wx, wxp)`

#### （4）调用Promise化之后的异步API

js

复制代码

`<van-button type="primary" bindtap="getInfo">主要按钮</van-button>`

js

复制代码

`async getInfo(){     const {data:res} = await wx.p.request({         method:'GET',         url:'https://www.escook.cn/api/get',         data:{name:'zx',age:20}     })     console.log(res); },`

十二、全局数据共享
---------

### 1.什么是全局数据共享

**全局数据共享**(又叫做：状态管理)是为了解决**组件之间数据共享**的问题。

开发中常用的全局数据共享方案有：Vuex、Redux、MoboX等。

### 2.小程序中的全局数据共享方案

在小程序中，可使用mobx-miniprogram配合mobx-miniprogram-bindings实现全局数据共享。其中：

*   mobx-miniprogram 用来创建Store实例对象
*   mobx-miniprogram-bindings 用来把Store中的共享数据或方法，绑定到组件或页面中使用。

### 3.Mobx

#### （1）安装 MobX 相关的包

在小程序项目中，可以通过 npm 的方式引入 MobX 。如果还没有在小程序中使用过 npm ，先在小程序目录中执行命令：

csharp

复制代码

`npm init -y`

引入 MobX ：

css

复制代码

`npm install --save mobx-miniprogram@4.13.2 mobx-miniprogram-bindings@1.2.1`

注意：MobX 相关的包安装完毕之后，记得 **删除 miniprogram\_npm 目录**后，**重新构建 npm**。

#### （2）创建 MobX 的 Store实例

在项目文件夹下创建store文件夹，再在文件夹下创建store.js文件：

js

复制代码

`// 在这个js文件中，专门创建 store的实例对象 import {action, observable} from 'mobx-miniprogram' export const store =observable({     numA:1,     numB:2,     // 计算属性,get的意思是只读     get Sum(){         return this.numA + this.numB     },     // action 方法，用来修改 store 中的数据     updateNum1:action(function (step) {         this.numA += step       }) })`

#### （3）将Store中的成员绑定到`页面`中

#### （4）在页面上使用 Store中的成员

js

复制代码

`<van-button type='primary' bindtap="handleNum" data-step="{{1}}">numA + 1</van-button> <van-button type='warning' bindtap="handleNum" data-step="{{-1}}">numA - 1</van-button>`

js

复制代码

`import {createStoreBindings} from 'mobx-miniprogram-bindings' import {store} from '../../store/store' Page({     onLoad() {         this.storeBindings = createStoreBindings(this,{             store,             fields:['numA','numB','sum'],             actions:['updateNum1']         })     },     onUnload:function () {         this.storeBindings.destroyStoreBindings()     },     handleNum(e){         // 直接调用方法即可         this.updateNum1(e.target.dataset.step)     }, })`

#### （5）将Store中的成员绑定到`组件`中

js

复制代码

`import { storeBindingsBchavior } from 'mobx-miniprogram-bindings' import { store } from '././store/store' Component({     behaviors:[ storeBindingsBchavior ],//通过storeBindingsBchavior 来实现自动绑定     storeBindings:{         //指定要绑定的Store         store,         fields:{   //指定要绑定的字段数据             numA:()=>store.numA, //绑定字段的第1种方式             numB:(store)=>store.numB, //绑定字段的第2种方式                   sum:'sum'  //绑定字段的第3种方式         },         actions:{  //指定要绑定的方法             updateNum2:'updateNum2'         }     } })`

十三、分包
-----

### 1.什么是分包

分包指的是把一个完整的小程序项目，按照需求划分为不同的子包，在构建时打包成不同的分包，用户在使用时按需进行加载。

### 2.分包的好处

对小程序进行分包的好处主要有以下两点：

*   可以优化小程序首次启动的下载时间
*   在多团队共同开发时可以更好的解耦操作

### 3.分包前项目的构成

分包前，小程序项目中所有的页面和资源都被打包到了一起，导致整个项目体积过大，影响小程序首次启动的下载时间。

![截屏2022-11-21 下午10.35.04.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a532227db89243749b723105ed806f72~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 4.分包后项目的构成

![截屏2022-11-21 下午10.38.08.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c1144658934047c38327a466f4fb59b5~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

![截屏2022-11-21 下午10.38.17.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/742613b33fbd457eb8d023875ed2beaa~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 5.分包的加载规则

![截屏2022-11-21 下午10.40.27.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7281f78288cc473f85e40f676dd7abe4~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 6.分包的体积限制

![截屏2022-11-21 下午10.41.32.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/3b348ea1aa7049ecb506ca63e15580d3~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 7.使用分包

#### （1）配置方法

![截屏2022-11-21 下午10.45.56.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/73ebc621f5d0487f9f517418b7c829a5~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

![截屏2022-11-21 下午11.01.38.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f12d10e9822946d3a95ddadbd4e16775~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### （2）打包原则

![截屏2022-11-21 下午11.13.54.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e84f8dc4cab2470da34099f96f29f1fc~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### （3）引用原则

①主包**无法引用**分包内的私有资源

②分包之间**不能相互引用**私有资源

③分包**可以引用**主包内的公共资源

### 8.独立分包

#### （1）什么是独立分包

![截屏2022-11-21 下午11.17.49.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ff9ff359021041b5a128622c2562ee3a~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### （2）独立分包和普通分包的区别

最主要的区别：是否**依赖于主包**才能运行。

*   普通分包必须依赖于主包才能运行
*   独立分包可以在不下载主包的情况下，独立运行

#### （3）独立分包的应用场景

![截屏2022-11-21 下午11.20.29.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/cfdab397c6594fb5a5fb4bdec914fcb9~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### （4）独立分包的配置方法

![截屏2022-11-21 下午11.21.33.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/2d086ed6838d485f9a084fe369982c1a~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### （5）引用原则

![截屏2022-11-21 下午11.23.16.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f7254324d68d4db2bbc8145ac280feac~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 9.分包预下载

#### （1）什么是分包预下载

分包预下载指的是：在进入小程序的某个页面时，**由框架自动预下载可能需要的分包**，从而提升进入后续分包页面时的启动速度。

#### （2）配置分包的预下载

预下载分包的行为，会在进入指定的页面时触发。在`app.json`中，使用`preloadRule`节点定义分包的预下载规则。实例代码如下：

js

复制代码

`{     preloadRule": { // 分包预下载的规则         "pages/contact/contact": { // 触发分包预下的页面路径             // network 表示在指定的网络模式下进行预下载,             // 可选值为: all(不限网络) 和 wifi(仅 wifi 式下进行预下载)             // 默认值为: wifi             "network":"all",             // packages 表示进入页面后，预下载哪些分包             // 可以通过 root 或 name 指定预下哪些分包             "packages":["pkgA"]         }     } }`

#### （3）分包预下载的限制

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/3aea19c0d4fb443c95a46a1d631270ff~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

#### 案例六--自定义tabBar

网址：[developers.weixin.qq.com/miniprogram…](https://link.juejin.cn?target=https%3A%2F%2Fdevelopers.weixin.qq.com%2Fminiprogram%2Fdev%2Fframework%2Fability%2Fcustom-tabbar.html "https://developers.weixin.qq.com/miniprogram/dev/framework/ability/custom-tabbar.html")

注意：custom-tab-bar/index.js 创建的是 组件Component！

跟着视频没写出来，去b站找了详细的视频，实现了效果。

**至此，小程序的理论课程结束了。**

配套的uniapp项目：

开发文档：[www.escook.cn/docs-uni-sh…](https://link.juejin.cn?target=https%3A%2F%2Fwww.escook.cn%2Fdocs-uni-shop%2F "https://www.escook.cn/docs-uni-shop/")

项目源码地址：[gitee.com/qiuyan-yin/…](https://link.juejin.cn?target=https%3A%2F%2Fgitee.com%2Fqiuyan-yin%2Funi-shop.git "https://gitee.com/qiuyan-yin/uni-shop.git")

本文转自 <https://juejin.cn/post/7146956663633739784#heading-36>，如有侵权，请联系删除。