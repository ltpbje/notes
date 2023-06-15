
<img src="C:\Users\19836\OneDrive\obsidian\pdf\HtmlCSS(自学">.pdf"> 





表格边框合并

**`border-collapse`** [CSS](https://developer.mozilla.org/zh-CN/docs/Web/CSS) 属性是用来决定表格的边框是分开的还是合并的。在分隔模式下，相邻的单元格都拥有独立的边框。在合并模式下，相邻单元格共享边框。

合并（*collapsed*）模式下，表格中相邻单元格共享边框。在这种模式下，CSS 属性[`border-style`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-style) 的值 inset 表现为槽，值 outset 表现为脊。

分隔（*separated）*模式是 HTML 表格的传统模式。相邻单元格都拥有不同的边框。边框之间的距离是通过 CSS 属性 [`border-spacing`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-spacing) 来确定的。

# background-image

[CSS](https://developer.mozilla.org/zh-CN/docs/Web/CSS) **`background-image`** 属性用于为一个元素设置一个或者多个背景图像。

## Web开发-CSS3

## CSS之2D转换

###  transform                                                                                          

英 [trænsˈfɔː(r">m]

- **v.**使改变形态；使改变外观（或性质）；使改观

- **n.**【数】变换式；【化】反式

- **网络**转换；转化；转变，变革

  ### **rotate**    旋转

  美 [ˈrəʊˌteɪt]

  英 [rəʊˈteɪt]

  - **v.**旋转；转动；轮换；使…轮流

  - **网络**循环；旋转命令；轮转

  - # **deg**   角度

    美 ['deɡ]

    英 ['deɡ]

    - n.********度********；变性

    - **网络**二甘醇；角度；的

      

      

      #### **scale** 	缩放

      美 [skeɪl]

      英 [skeɪl] 

      - **n.**秤；比例尺；范围；刻度
      - **v.**攀登；到达…顶点；去鳞；刮除牙石
      - **网络**缩放；规模；音阶

**scale缩放不会影响其他盒子而且可以设置缩放的中心点**

**中心点**

`transform-origin: left bottom;`

### transform复合写法

**transform:可以复合在一起写(但最好位移放在最前面否则会影响其他属性">**

**translate**-**rotate******- scale****   

 **位移**			**旋转** 		**缩放**	

## **CSS3动画 **

### **动画的基本使用**

先**定义**再**使用**  **由多个节点来控制**

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959446.png" alt="image-20230415191555544" />

### **利用keyframe来定义动画**

**from to 等同于 0% 到 100%**

**keyframe可以做多个状态的变化关键帧**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959447.png">

### **动画的使用**

```css
/* 动画的定义 */
        @keyframes move {
            /* 开始状态 */
            0% {
                transform: translate(0, 0">;
            }

            /* 结束状态 */
            100% {
                transform: translate(100px, 0">;
            }
        }

        /* 动画的使用 */
        div {
            height: 100px;
            width: 100px;
            /* 引用动画名称 */
            animation-name: move;
            /* 设置动画持续时间 */
            animation-duration: 2s;
            background-color: pink;
        }
```

### 动画序列

```css
 div {
            height: 200px;
            width: 200px;
            margin: 20px auto;
            animation-name: move;
            animation-duration: 10s;
            background-color: pink;
        }

        /* 动画序列 */
        /* @keyframes move {
            from {
                transform: translateX(0">;
            }

            to {
                transform: translateX(700px">;
            }
        } */
        @keyframes move {
            0% {
                transform: translate(0, 0">;
            }

            25% {
                transform: translate(500px, 0">;
            }

            50% {
                transform: translate(500px, 500px">;
            }

            75% {
                transform: translate(0px, 500px">;
            }

            100% {
                transform: translate(0, 0">;
            }
        }
```

### 动画常用属性
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959448.png">

```css
@keyframes move {
            from {
                transform: translate(0, 0">;
            }

            to {
                transform: translate(500px, 0">;
            }
        }

        div {
            height: 200px;
            width: 200px;
            background-color: pink;
            /* 动画名称  必须加的*/
            animation-name: move;
            /* 持续时间 必须加的*/
            animation-duration: 2s;
            /* 速度曲线 */
            animation-timing-function: ease;
            /* 动画何时开始 (延迟播放"> */
            animation-delay: 0.1s;
            /* 动画播放的次数 默认是1  实现循环用infinite */
            animation-iteration-count: infinite;
            /* 在下一周期是否逆向播放  默认是normal*/
            animation-direction: alternate;
            /* 规定动画是否运行或暂停 running 经常和hover一起使用 */
            animation-play-state: running;
            /* 规定动画结束后的状态 */
            /*backwards 返回原来的状态 */
            animation-fill-mode: forwards;
        }

        div:hover {
            /* 规定动画是否运行或暂停  paused */
            animation-play-state: paused;
        }
```

#### 动画属性的复合运用

**linear 线性的**
**动画简写属性**
**animation :名字 持续时间 运动曲线 开始时间 播放次数 是否反方向 规定动画结束后的状态;**
animation:  myfirst  5s  linear  2s  infinite  alternate forwards;
简写属性里面不包含animation-play-state
暂停动画:animation-play-state: puased;经常和鼠标经过等其他配合使用想要动画走回来，而不是直接跳回来:animation-direction : alternate盒子动画结束后，停在结束位置: animation-fill-mode : forwirds

```css
 @keyframes move {
            from {
                transform: translate(0, 0">;
            }

            to {
                transform: translate(500px, 0">;
            }
        }

        div {
            height: 200px;
            width: 200px;
            background-color: pink;
            animation: move 2s linear 0.1s infinite alternate forwards;
            /* 名字 持续时间 运动曲线 开始时间 播放次数 是否反方向 规定动画结束后的状态*/
        }

        div:hover {
            /* 规定动画是否运行或暂停  paused */
            animation-play-state: paused;
        }
```



**box-shadow X 轴偏移量、Y 轴偏移量、模糊半径、扩散半径  颜色**

#### 大数据热点图案例



#### 速度曲线细节-==步长==

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959449.png">

##### **一个元素可以添加多个动画**

##### **熊大奔跑案例**

```
 /* 一个元素可以使用两个动画 */
            animation: bear 1s steps(8"> infinite, move 3s linear forwards;
```



## 复习

### ==权重==

**内联样式（即在HTML标签中使用style属性设置的样式"> ——>1000**

**ID选择器                                                                          ——>  100**

**类选择器    属性选择器                                                     ——>    10**

**标签选择器                                                                       ——>      1**

### ==**img  **==

==**是行内元素**== 

**是图像嵌入元素**

### **==opacity透明度==**

**指定一个元素的不透明度 初始值为1  范围为0~1**

### ==属性选择器==

**实例**

```css
 /* input[value] {
            color: pink;
        } */
	div[class^=pulse]{
    
	}
        input[value="请输入文本"] {
            color: pink;
        }
 
```

```
<!-- <input type="text" value="请输入文本">
    <input type="text"> -->
    <input type="text" value="请输入文本">
    <input type="text" value="请输入">
    <div class="pulse1"></div>
    <div class="pulse2"></div>
    <div class="pulse3"></div>
```

```
[attr]
```

**表示带==有以 *attr* 命名==的属性的元素。**

```
[attr=value]
```

**表示带有以 *attr* 命名的属性，且属性值为 *value* 的元素。**

```
[attr~=value]
```

**表示带有以 *attr* 命名的属性的元素，并且该属性是一个以空格作为分隔的值列表，其中至少有一个值为 *value*。**

```
[attr|=value]
```

**表示带有以 *attr* 命名的属性的元素，属性值为“value”或是以“value-”为前缀（`-` 为连字符，Unicode 编码为 U+002D）开头。典型的应用场景是用来匹配语言简写代码（如 zh-CN、zh-TW 可以用 zh 作为 value）。**

```
[attr^=value]
```

**表示带有以 *attr* 命名的属性，且属性值是以 *value* 开头的元素。**

```
[attr$=value]
```

**表示带有以 *attr* 命名的属性，且属性值是以 *value* 结尾的元素。**

```
[attr*=value]
```

**表示带有以 *attr* 命名的属性，且属性值至少包含一个 *value* 值的元素。**

```
[attr operator value i]
```

**在属性选择器的右方括号前添加一个用空格隔开的字母 `i`（或 `I`），可以在匹配属性值时忽略大小写（支持 ASCII 字符范围之内的字母）。**

### 强制一行显示 

​      `white-space: nowrap;`

### 利用Vertical-align实现垂直方向水平居中 

**当图片的高度大于文字的高度时用line-height无法完美实现垂直方向上的居中效果因为图片的底部对的是文字的基线**

**此时要利用Vertical-align:middle来实现居中效果**

### 盒子阴影box-shadow

![image-20230422192316016<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959450.png">

```
/*   水平阴影的位置  垂直阴影的位置  模糊距离 阴影的尺寸 颜色 外部阴影 */
            box-shadow: 0 0 2px 3px rgba(0, 0, 0, .3">;
```



### 文字阴影 text-shadow
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959451.png">

### 圆角边框


<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959452.png">


<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959453.png">

### box-sizing

`content-box` 是**默认值**。如果你设置一个元素的宽为 100px，那么这个元素的内容区会有 100px 宽，并且任何边框和内边距的宽度都会被增加到最后绘制出来的元素宽度中。

`border-box` 告诉浏览器：你想要设置的边框和内边距的值是包含在 width 内的。也就是说，如果你将一个元素的 width 设为 100px，那么这 100px 会包含它的 border 和 padding，内容区的实际宽度是 width 减去 (border + padding"> 的值。大多数情况下，这使得我们更容易地设定一个元素的宽高。

## CSS3之3D转换





#### 三维坐标系

**x轴 水平==向右== 为正**

**y轴 垂直==向下== 为正**

**z轴 垂直屏幕==向外== 为正**

#### 3D 移动-==translate==

**3D转换==配合透视才能生效==-==才能产生立体感==-perspective  透视需要加在需要3D转换的元素的==父盒子==上**

```
  /*3D转换简写 translate3d  */
            transform: translate3d(200px,200px,200px">;
             body {
     body {
           /* 3D转换配合透视才能生效-perspective  透视需要加在需要3D转换的元素的父盒子上*/
            perspective: 200px;
        }

        div {
            height: 200px;
            width: 200px;
            margin: 40px auto;
            background-color: pink;
            /*3D转换简写 translate3d  */
            transform: translateZ(10px">;
        }
```

#### 透视 也称视距 

**==透视== 就是眼睛到屏幕的距离  越近物体越大 越远物体越小**  ![image-20230418081619150<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959454.png">

**d 为视距 眼睛到屏幕的距离 **

**z 为translateZ的值即为物体到屏幕的距离**

#### 3D旋转-==rotate==

#### 左手准则
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959455.png">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959456.png">

#### 3D呈现 ==transform-style== 

**让元素的==子元素物体呈现==**==3D效果==

**transform-style:==flat== ==子元素不开启3d立体空间==  ==默认的==**

**transform-style: preserve-3d;子元素开启立体空间 代码写给父级，但是影响的是子盒子**

#### trasnsform复合属性

**先移动==translate==后旋转==rotate==**

```
 旋转木马
 section div:nth-child(2"> {

     /* 先旋转在移动 旋转之后对应元素的坐标系会发生变化*/

     transform: rotateY(60deg"> translateZ(300px">;

    }
```



## 浏览器私有前缀
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959457.png">

# 移动端Web开发

## body初始化css文件

```
body {
    max-width: 540px;
    min-width: 320px;
    margin: 0 auto;
    font: normal 14px/1.5 Tahoma, "Lucida Grande", Verdana, "Microsoft Yahei", STXihei, hei;
    color: #000;
    background: #f2f2f2;
    overflow-x: hidden;
    -webkit-tap-highlight-color: transparent;
}
```



## 视口

视口( viewport）就是浏览器显示页面内容的屏幕区域。视口可以分为布局视口、视觉视口和理想视口

### 布局视口layout viewport

一般移动设备的浏览器都默认设置了一个布局视口，用于解决早期的PC端页面在手机上显示的问题。iOS,Android基本都将这个视口分辨率设置为980px，所以PC上的网页大多都能在手机上呈现，只不过元素看上去很小，一般默认可以通过手动缩放网页。

### 视觉视口visual viewport

字面意思，它是**用户正在看到的网站的区域**。注意∶是网站的区域。
我们可以通过缩放去操作视觉视口，但不会影响布局视口，布局视口仍保持原来的宽度。

### 理想视口ideal viewport

为了使网站在移动端有最理想的浏览和阅读宽度而设定理想视口，对设备来讲，是最理想的视口尺寸
需要手动添写meta视口标签通知浏览器操作
meta视口标签的主要目的:**布局视口的宽度应该与理想视口的宽度一致，简单理解就是设备有多宽，我们布局的视口就多宽**

### meta视口标签

```
<meta name="viewport"
        content="width=device-width,initial-scale=1.0,maximum-scale=1.0,minimum-scale=1.0,user-scalable=0">
```
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959458.png">

### 标准的viewport设置
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959459.png">

**视口宽度和设备保持一致·**
**视口的默认缩放比例1.0**
**不允许用户自行缩放最大允许的缩放比例1.0·**
**最小允许的缩放比例1.0**

### 二倍图

**更多的物理像素压缩至一块屏幕**

**我们需要一个50*50像素(css像素">的图片直接放到我们的iphone8里面会放大2倍100*100就会模糊**

**我们采取的是放一个100*100的图片然后手动的把这个图片缩小为 50*50****

我们**准备的图片**比我们**实际需要**的**大小大2倍**，这就方式就是**2倍图**

```
 /* 我们需要一个50*50像素(css像素">的图片直接放到我们的iphone8里面会放大2倍100*100就会模糊我们采取一个100*100的图片然后手动的把这个图片缩小为 50*50
我们准备的图片比我们实际需要的大小大2倍，这就方式就是2倍图 */
        img:nth-child(2"> {
            height: 50px;
            width: 50px;
        }
    </style>
</head>

<body>
    <!-- 模糊 -->
    <img src="./images/apple50(1">.jpg" alt="">
    <!-- 利用二倍图 清晰的 -->
    <img src="./images/apple100.jpg" alt="">
```


<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959460.png">

#### 多倍图

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959461.png">

### background-size-背景图片缩放

```
    div {
​      height: 50px;
​      width: 50px;
​      background: url(./images/apple100.jpg"> no-repeat;
​      background-size: 50px 50px;
​    }
```

## 移动端开发选择

**单独制作移动端页面**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959462.png">

**响应式兼容PC端移动端**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959463.png">

### 移动端技术解决方案


<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959464.png">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959465.png">

## 移动端常见布局

### 流式布局(百分比布局">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959466.png">

```
section {
            width: 100%;
            /*设置最大宽度 */
            max-width: 900px;
            /*设置最小宽度 */
            min-width: 700px;
        }

        section div {
            float: left;
            width: 40%;
            height: 300px;
        }
```

#### 二倍精灵图的使用

```
    /* 二倍精灵图 坐标变为实际测量的二分之一 */

    background: url(../images/jd-sprites.png"> no-repeat -83px -0px;
    /* 图片宽高变为原来的二分之一 */
    background-size: 200px;
```

#### 图片格式
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959467.png">

### flex布局
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959468.png">

#### flex布局原理
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959469.png">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959470.png">

#### flex布局父项属性
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959471.png">

#### flex主轴方向
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959473.png">

```
 display: flex;
            /* 主轴方向从左到右 */
            flex-direction: row;
            /* 主轴方向从右到左 */
            flex-direction: row-reverse;
            /* 主轴方向从上到下 */
            flex-direction: column;
            /* 主轴方向从下到上 */
            flex-direction: column-reverse;
```

####  ==justify-content==设置主轴上的子元素排列方式
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959474.png">

```
display: flex;
            /* 规定子元素在主轴上的排列方式 */
            /* 从左到右默认的排列方式 */
            /* justify-content: start; */
            /* 从右到左的排列方式 */
            /* justify-content: end; */
            /* 子元素延主轴居中的排列方式 */
            /* justify-content: center; */
            /* 平分剩余空间 */
            /* justify-content: space-around; */
            /* 先两边贴边再平分剩余空间 */
            /* justify-content: space-between; */
            height: 400px;
            width: 500px;
            background-color: pink;
```

#### flex-wrap 是否换行

```
display: flex;
            /* 默认不换行 */
            /* flex-wrap: nowrap; */
            /* 换行 */
            flex-wrap: wrap;
```



#### ==align-items==设置侧轴上的子元素排列方式(单行">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959475.png">

```
 display: flex;
            height: 400px;
            width: 500px;
            /* 侧轴方向垂直居中 */
            /* align-items: center; */
            /* 从上往下排 */
            /* align-items: flex-start; */
            /* 从下往上排 */
            /* align-items: flex-end; */
            /* 拉伸 沿侧轴方向拉伸 默认的 */
            align-items: stretch;
            align-items: center;
            background-color: pink;
```



#### ==align-content==设置侧轴上的子元素的排列方式（多行">

**单行无效**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959476.png">

```
 /* 从头部开始排列 */
            /* align-content: flex-start; */
            /* 从尾部开始排列 */
            /* align-content: flex-end; */
            /* 在侧轴中间显示 */
            /* align-content: center; */
            /* 子元素平分侧轴 */
            /* align-content: space-around; */
            /* 先子项分布在侧轴两头 再平分侧轴剩余空间 */
            /* align-content: space-between; */
            /* 子项元素平分父元素高度 */
            align-content: stretch;
            background-color: pink;
```



#### ==align-content==和==align-items==区别
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959477.png">



#### flex-flow(flex-direction 和 flex-wrap的复合属性">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959478.png">



#### flex属性

**定义子项目分配剩余空间**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959479.png">

#### align-self 控制子项自己在侧轴上的排列方式
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959480.png">



#### order 属性定义项目的排列顺序

**数值越小越靠前**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959481.png">

#### 携程案例
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959482.png">

#### 常见flex布局思路
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959483.png">

#### 背景线性渐变
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959484.png">

```
 /*背景渐变 必须加浏览器私有前缀 */
            /* background: -webkit-linear-gradient(left, green, red">; */
            /* 默认渐变方向从上到下 */
            /* background: -webkit-linear-gradient(pink, blue">; */
            background: -webkit-linear-gradient(left top, pink, blue">;
```
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959485.png">

### rem适配布局

#### rem基础

**em相对的是父元素的字体大小**

**rem相对的是Html元素的字体大小**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959486.png">

```
/* em单位 */
            /* 相对于父元素的字体大小 */
            /* width: 10em;
            height: 10em; */
            /* 相对于html元素的字体大小来改变宽高 */
            /* rem单位 */
            width: 10rem;
            height: 10rem;
```

#### 媒体查询
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959487.png">

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959488.png">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959489.png">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959490.png">

```
 /* 屏幕宽度小于等于800px时body的背景颜色才可以显现 */
        @media screen and (max-width:800px"> {
            body {
                background-color: pink;
            }
        }

        /* 屏幕宽度小于等于500px时body的背景颜色才可以显现 */
        @media screen and (max-width:600px"> {
            body {
                background-color: purple;
            }
        }
```

#### 媒体查询从小到大来写代码更加简洁
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959491.png">

#### 媒体查询+rem实现元素动态大小变化

```
  /* 媒体查询+rem实现元素动态大小变化 */
        @media screen and (min-width:350px"> {
            html {
                font-size: 400px;
            }
        }

        @media screen and (min-width:900px"> {
            html {
                font-size: 200px;
            }
        }

        .top {
            height: 1rem;
            font-size: 0.1rem;
            background-color: pink;
            text-align: center;
            line-height: 1rem;
        }
```

#### 引入资源
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959492.png">

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959493.png">

### Less

#### Less基础


<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959494.png">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959495.png">

#### less的使用
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959496.png">

##### **利用==easy less== 插件来将less编译为css文件**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959497.png">

##### ==less的嵌套==

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959498.png">

**伪元素选择器中的less使用方法**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959499.png">

##### ==less运算==
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959500.png">

**==less运算的注意事项==**

**符号左右两侧必须有空格隔开**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959501.png">

###### less运算的实例

**现在的==less语法中，除法需要加 (">== 或 . ，比如：
但不推荐  .  的写法，会提示波浪线错误，更推荐小括号(">**

```
div {
    // 加法的实现
    height: 200px + 100;
    // 乘法的实现
    width: (200px + 0"> * (3 / 2">;
    background-color: pink;
    border: @border solid #000;
}

img {
    // 运算符两边单位不同时会使用第一个元素的单位
    // 现在的less语法中，除法需要加(">或.，比如： 但不推荐.的写法，会提示波浪线错误，更推荐小括号(">
    display: block;
    height: (50rem / @baseFont">;
    width: 50rem ./ @baseFont;
}
```
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959502.png">

### rem适配方案
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959503.png">

#### 实际开发适配方案
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959504.png">

#### rem适配方案技术的使用
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959505.png">

##### 适配方案1
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959506.png">


<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959507.png">

**rem适配方案**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959508.png">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959509.png">

## 苏宁移动端

### rem适配方案1
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959510.png">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959512.png">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959513.png">

```
// body样式
body {
    min-width: 320px;
    width: 15rem;
    margin: 0 auto;
    line-height: 1.5;
    font-family: Arial, Helvetica;
    background: #F2F2F2;
}
```

```
// 页面元素rem的计算方式是页面元素的px除于html的字体大小
// search-content
.search-content {
    position: fixed;
    top: 0;
    width: 15rem;
    height: (88rem / 50">;
}
```

### rem适配方案2(更简单">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959514.png">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959515.png">

### VScode px转换rem插件 cssrem
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959516.png">

## 黑马面面

### 2.5 swiper 插件使用

官网地址：<https://www.swiper.com.cn/>

- 下载需要的css和js文件  html页面中 引入相关文件
- 官网找到类似案例，复制html结构，css样式  js 语法
- 根据需求定制修改模块

## 响应式开发

#### 响应式开发原理
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959517.png">

#### 响应式布局容器
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959518.png">

```
.container {
            height: 100px;
            background-color: pink;
            margin: 0 auto;
        }

        /* 手机超小屏幕 小于768 宽度设置为100% */
        @media screen and (max-width:767px"> {
            .container {
                width: 100%;
            }
        }

        /* 平板 小屏幕大于等于768 设置宽度为750px */
        @media screen and (min-width:768px"> {
            .container {
                width: 750px;
            }
        }

        /* 中等屏幕大于等于992px 设置宽度为970px   */
        @media screen and (min-width:992px"> {
            .container {
                width: 970px;
            }
        }

        /* 中等屏幕大于等于1200px 设置宽度为1170px   */
        @media screen and (min-width:1200px"> {
            .container {
                width: 1170px;
            }
        }
    </style>
</head>

<body>
    <div class="container"></div>
```

#### Bootstraps前端开发框架

##### Bootstrap简介

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959519.png">

**bootstrap的优点**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959520.png">

**bootstrap版本**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959521.png">

###### **创建文件夹结构**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959522.png">

###### **创建html骨架结构**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959523.png">

###### **引入相关样式文件**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959524.png">

```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!--[if lt IE 9]>
          <script src="https://cdn.jsdelivr.net/npm/html5shiv@3.7.3/dist/html5shiv.min.js"></script>
          <script src="https://cdn.jsdelivr.net/npm/respond.js@1.4.2/dest/respond.min.js"></script>
        <![endif]-->
    <!-- 一定不要忘记引入bootstrap 的样式文件 -->
    <link rel="stylesheet" href="./bootstrap/css/bootstrap.min.css">
    <title>Document</title>
</head>
```

**container布局容器**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959525.png">

###### **栅格系统 container被分为12份**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959526.png">

###### 列嵌套

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959527.png">

###### 列偏移

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959528.png">

```
<div class="container">
        <div class="col-md-3">左侧</div>
        <div class="col-md-3 col-md-offset-6">右侧</div>
    </div>
    <div class="container">
        <div class="col-md-2 col-md-offset-5">中间</div>
    </div>
```

###### 列排序
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959529.png">

```
<div class="container">
        <div class="col-md-5 col-md-push-7">左侧</div>
        <div class="col-md-7 col-md-pull-5">右侧</div>
    </div>
```

###### **响应式工具**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959530.png">

```
<div class="container">
        <div class="row">
            <div class="col-md-3 visible-xs">左侧</div>
            <div class="col-md-3 hidden-lg">右侧</div>
        </div>
```

## 阿里百秀案例
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959531.png">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959532.png">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959533.png">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959534.png">

```
/* 屏幕进入小屏幕和超小屏幕时 让nav里面的li浮动起来 */
@media screen and (max-width:991px"> {
    .nav li {
        float: left;
        width: 20%;
    }

    .news {
        margin-top: 10px;
    }
}

/* 屏幕进入超小屏幕时 让文字变小*/
@media screen and (max-width:767px"> {
    .nav a {
        padding-left: 0 !important;
    }

    .nav li {
        font-size: 10px;
    }

    article .news ul li:first-child {
        width: 100%;
    }

    article .news ul li:nth-child(n+2"> {
        width: 50%;
    }

    .publish h3 {
        font-size: 14px;
    }
}
```

## vw  / vh
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959535.png">

**vw适配原理**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959536.png">

**vh适配原理**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959537.png">

**px转为vw**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959538.png">

## m.bilibili项目

**后面的定位会覆盖前面的定位**

**vmin 可以照顾手机端横屏和竖屏的显示效果 取屏幕宽度和高度的最小值**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959539.png">





## 二、指定css文件保存路径

1. 点击设置 扩展设置<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091959540.png">

```
// 相对路径
    "less.compile": {
        "out": "../css/"
    }
```

