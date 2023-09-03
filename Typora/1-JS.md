# JS基础-ECMAScript

## 逻辑运算符

**逻辑与 逻辑或** 

```
  // 逻辑与 a&&b 若a为真 返回b a为假返回a 
        console.log(2 && 3)//返回3
        // 逻辑或 a||b 若a为真 返回a a为假返回b
        console.log(2 > 1 || 3 < 2)// true
        console.log(2 > 1 && 3 < 2)//flase
```



## 对象

### 使用原型(prototype">创建对象

当我们创建一个函数时，函数就会自动拥有一个`prototype`属性，这个属性的值是一个对象，这个对象被称为该函数的原型对象。也可以叫做原型。

```
function Store("> {};
Store.prototype.name = "SF Express";
Store.prototype.locaion = "Hong Kong";
Store.prototype.salesVolume = 1200000000;
// 创建对象
var myStore = new Store()
// 创建一个新的对象
var hisStore = new Store()
hisStore.name = "STO Express";    // 覆盖了原来的name属性
```

### 属性的检测

属性的检测指检查对象是否有某个属性或者方法，需要使用运算符`in`，`in`的左侧是属性或者方法名，右侧是检查对象，对象有该属性或者方法则返回

```
var school = {
    name:"SJTU",
    location:"ShangHai",
    studentNum:40000,
    display:function("> {
          console.log(this.name)
    }
};
// 检测属性
console.log("name" in school)    // 输出true
console.log("sales" in school)    // 输出false
// 检测方法
console.log("display" in school)    // 输出true
console.log("print" in school)    // 输出false
```

`true`，否则返回`false`

### Date对象

```
展示了用来创建一个日期对象的多种方法
var today = new Date()
var birthday = new Date('December 17, 1995 03:24:00')
var birthday = new Date('1995-12-17T03:24:00')
var birthday = new Date(1995, 11, 17)
var birthday = new Date(1995, 11, 17, 3, 24, 0)
```

### 内置对象

#### Math对象

##### Math对象生成随机数

```
// 生成一个0到10的随机数
        let getRandom = Math.floor(Math.random()11)
        // 生成一个3到10的随机数
        // let b = Math.floor(Math.random()*(10 - 3 + 1) + 3)
        let b = Math.floor(Math.random()*(10 - 3 + 1)) + 3;
        // 生成一个N到M的随机数
        // let c = Math.floor(Math.random()*(M - N + 1) + N)
        // let c = Math.floor(Math.random()*(M - N + 1) ) + N;
        console.log(b)
```

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909979.png" alt="image-20230425201045707" />

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909981.png">**

### 数据类型

**==值类型== 存储的值的本身**

**==引用类型== 存储的仅是地址**

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909982.png">

#### 堆和栈

**引用数据类型的值实际存储在堆中**

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909983.png" alt="image-20230427192643306" style="zoom:50%;" />

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909984.png" alt="image-20230427192357053" style="zoom: 67%;" />

# Web-APIs

## 变量的声明

**const优先**

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909985.png">

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909987.png">

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909988.png">

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909989.png">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909990.png">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909991.png">

## 总结 

**数组和对象建议用const来声明**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909992.png">

## 1.DOM

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909993.png"><img src ="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909994.png">

**DOM树**

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909995.png">

### DOM对象

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909996.png">

```
 //浏览器根据HTML标签自动生成了DOM对象
        // 显示选中的第一个标签 query查询 Selector选择器
        let div = document.querySelector('div')
        // 在控制台显示DOM对象
        console.dir(div)
```

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909997.png">

### ==获取DOM元素==

****



**根据CSS选择器来获取DOM元素**

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909998.png">

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909999.png">

**修改元素内容·**

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909000.png">

```js
// 获取元素
        const box = document.querySelector('.box')
        // 修改元素内容
        // box.innerText = '我是盒子'//修改文字内容
        // console.log(box.innerText)//获取文字内容
        // box.innerText = '<b>我是盒子</b>';//innerText 不能解析HTML标签元素
        // box.innerHTML = '<b>我是盒子</b> '//innerHTML可以解析HTML标签元素
```

### 操作元素常用属性

```js
const img = document.querySelector('img')
        img.src = './images/2.webp';
        img.title = 'pink老师的艺术照'
```
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909001.png">

### 操作元素样式属性

**小驼峰命名法**
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909002.png">

### 操作类名来操作css
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909003.png">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909005.png">

```
// 获取元素
        const div = document.querySelector('div')
        // 添加类名
        div.className = 'box nav';
```

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909006.png">

### ==通过classlist修改样式==

==classList contains()== 方法解释

该`contains()`方法将检查元素的`class`属性并检查它是否包含特定的类名。

您需要将要检查的类名作为其参数传递。`true`如果类名存在或`false`不存在，该方法将返回。

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909007.png">

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909008.png">

```
 const div = document.querySelector('div')
        // 追加类add()
        // div.classList.add('nav')
        //删除类名
        // div.classList.remove('box')
        // 切换类toggle 有则删除无则添加
        // div.classList.toggle('box')
        div.classList.toggle('nav')
```
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909009.png">

### 随机轮播图

```
/* 生成随机数 */
    const random = Math.floor(Math.random()sliderData.length)
    /* 1.获取图片元素 */
    const img = document.querySelector('.slider-wrapper img')
    img.src = sliderData[random].url;
    /*  2.获取标题元素 */
    const p = document.querySelector('.slider-footer p')
    p.innerHTML = sliderData[random].title;
    /* 3.获取slider-footer元素 */
    const footer = document.querySelector('.slider-footer')
    /* 修改背景颜色 */
    footer.style.backgroundColor = sliderData[random].color;
    /* 获取对应的小圆点 */
    const li = document.querySelector(`.slider ul li:nth-child(${random + 1}">`)
    /* 为获取的li添加active 类名 */
    li.classList.add('active')
```

### 操作表单元素的属性

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909010.png">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909011.png">

### 自定义属性
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909012.png">

### 定时器函数

```
 // setInterval(函数,间隔时间">时间单位是毫秒
        setInterval(function ("> {
            console.log('计时')
        }, 1000)
        // 函数会自动调用不必再次调用否则会出错
        function fn("> {
            console.log('计时1')
        }
        // setInterval(fn(">, 1000)
        // setInterval(函数, 间隔时间">返回的是一个数字代表的是第几个计时器
        let m = setInterval(fn, 1000)
        console.log(m)
        // 停止定时器
        clearInterval(m)
```
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909013.png">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909014.png">

### 轮播图定时器版
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909015.png">

## 2.DOM 

### 事件监听
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909016.png">

**事件监听的实质: 就是让程序检测是否有事件产生，一旦有事件触发就立即调用一个函数做出响应，也称为注册事件**

**三要素:事件源 事件类型 事件调用的函数**


<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909017.png">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909018.png">

### 随机点名案例
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909019.png">

### 事件监听关于const的小问题

```
 const btn = document.querySelector('button')
        btn.addEventListener('click', function () {
            // js 有垃圾回收机制该函数执行完之后该函数产生的数据会被清除
            const random = Math.random()
            console.log(random)
        })
```

### 事件监听版本(了解即可)

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909020.png" alt="image-20230508084245786" />

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909021.png" alt="image-20230508084641429" />

### 事件类型

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909022.png">

```
  const div = document.querySelector('div')
        // 鼠标移入事件源 触发事件
        div.addEventListener('mouseenter', function () {
            console.log(`轻轻的我来了`)
        })
        // 鼠标离开事件源 触发事件
        div.addEventListener('mouseleave', function () {
            console.log(`轻轻的我走了`)
        })

```

### 事件对象
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909023.png">

#### 获取事件对象
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909024.png">
<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909026.png">

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305091909027.png" alt="image-20230509100302577" />

**trim()方法清除字符串两侧的空格**

```
// trim()方法清除字符串两侧的空格
        if (tx.value.trim() !== '') {
          item.style.display = 'block';
          text.innerHTML = tx.value;
        }
```

### 环境对象

目标:能够分析判断函数运行在不同环境中this所指代的对象

环境对象:指的是函数内部特殊的变量 **this**，它代表着当

前函数运行时所处的环境作用:弄清楚this的指向，可以让我们代码更简洁

函数的调用方式不同，this指代的对象也不同

> **==【谁调用, this就是谁】==是判断this指向的粗略规则   代表当前函数运行时所处的环境** ![image-20230509210158832](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109101.png)



### 回调函数

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109102.png" alt="image-20230509205835098" />

>
>
><img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109103.png" alt="image-20230509210340947" />
>
>

### tab栏切换案例

```
   // 1.导航栏
    const as = document.querySelectorAll('.tab-nav a');
    //2.为导航栏中的a添加事件监听 
    for (let i = 0; i < as.length; i++) {
      as[i].addEventListener('mouseenter', function () {
        document.querySelector('.tab-nav .active').classList.remove('active');
        this.classList.add('active');
     // 3.内容的切换 干掉其他的添加新的
        document.querySelector('.tab-content .active').classList.remove('active');
        document.querySelector(`.tab-content .item:nth-child(${i + 1})`).classList.add('active');
      })
    }
     
```

### 表单全反选案例

```
  // 一. 业务一 全选控制小按钮功能
    // 获取全选框
    const checkAll = document.querySelector("#checkAll");
    const cks = document.querySelectorAll(".ck");
    // 添加事件监听
    checkAll.addEventListener('click', function () {
      for (let i = 0; i < cks.length; i++) {
        //遍历所有小复选框 使其小复选框的checked = 全选框的checked
        cks[i].checked = checkAll.checked;
      }
      // 二. 小复选框三个全选时 全选框实现自动勾选
    })
    for (let i = 0; i < cks.length; i++) {
      cks[i].addEventListener('click', function () {
        checkAll.checked = (document.querySelectorAll('.ck:checked').length === cks.length);
      }
      )
    }
```



#### CSS伪类选择器

```
 /* 选择被勾选的复选框 */
        .ck:checked {
            height: 20px;
            width: 20px;
        }
           <input type="checkbox" name="" class="ck">
    <input type="checkbox" name="" class="ck">
    <input type="checkbox" name="" class="ck">
```

## 3.DOM

### 事件流



<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109104.png" alt="image-20230511082635761" />

#### 捕获阶段(了解即可)

**从根节点到触发事件的节点依次执行同名事件**

> ![image-20230511083906737](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109105.png)
>
> ```
> · const fa = document.querySelector(".father");
>         const son = document.querySelector('.son');
>         document.addEventListener('click', function () {
>             alert("我是爷爷");
>         }, true)
>         fa.addEventListener('click', function () {
>             alert("我是爸爸");
>         }, true)
>         son.addEventListener('click', function () {
>             alert("我是儿子");
>         }, true)
> ```
>
> 



#### 冒泡阶段

> ![image-20230511084826482](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109107.png)
>
> ```
>   // 冒泡阶段
>         const fa = document.querySelector(".father");
>         const son = document.querySelector('.son');
>         document.addEventListener('click', function () {
>             alert("我是爷爷");
>         })
>         fa.addEventListener('click', function () {
>             alert("我是爸爸");
>         })
> 
>         son.addEventListener('click', function (e) {
>             alert("我是儿子");
>             // 阻止事件流动
>             e.stopPropagation();
>         })
> 
> ```
>
> 

### 事件解绑

**L0 事件解绑方法**

```
const btn = document.querySelector('button');
        // L0事件解绑
        btn.onclick = function () {
            alert('点我呀');
            btn.onclick = null;
        }
```

**L2事件解绑方法**

**匿名函数无法被解绑**

```
  // L2事件解绑方法
        btn.addEventListener('click', function fn() {
            alert('点我呀');
            btn.removeEventListener('click', fn)
        })
```

![image-20230511094003946](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109108.png)

```
 const fa = document.querySelector('.father');
        const son = document.querySelector('.son');
        fa.addEventListener('mouseover', function () {
            console.log('鼠标经过');
        })
        fa.addEventListener('mouseout', function () {
            console.log('鼠标离开');
        })
```

### 事件委托

**事件委托是利用事件流的特征解决一些开发需求的知识==一种技巧==**

> **优点:减少注册次数，可以提高程序性能**
>
> **原理:事件委托其实是利用事件冒泡的特点。**
>
> **给父元素注册事件，当我们触发子元素的时候，会冒泡到父元素身上，从而触发父元素的事件**
>
> **实现:事件对象.target.tagName可以获得真正触发事件的元素**
>
> ```
>   const ul = document.querySelector('ul');
>         ul.addEventListener('click', function (e) {
>             // console.log(e.target)
>             // console.dir(e.target.tagName);
>             if (e.target.tagName === 'LI') {
>                 // Event 接口的 target 只读属性是对事件分派到的对象的引用
>                 e.target.style.color = 'red';
>             }
>         })
> ```

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109109.png" alt="image-20230511101613576" />

#### 事件委托版tab栏切换

```
 const ul = document.querySelector('.tab-nav ul');
        // 一.导航栏切换业务
        ul.addEventListener('mouseover', function (e) {
            // 只有点到a时才会触发事件监听行为
            if (e.target.tagName === 'A') {
                // 排他原理
                document.querySelector('.tab-nav ul .active').classList.remove('active');
                e.target.classList.add('active');
                //二. 内容切换业务
                const i = +e.target.dataset.id;
                console.log(i);
                console.log(typeof (i));
                document.querySelector('.tab-content .active').classList.remove('active');
                document.querySelector(`.tab-content .item:nth-child(${i})`).classList.add('active')
            }
```

### 阻止默认行为

![image-20230511192517041](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109110.png)

![image-20230511192735421](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109111.png)

### 页面加载事件

1![image-20230511200304907](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109112.png)

```
 // 等待页面元素加载完毕后再执行回调函数
        window.addEventListener('load', function () {
            const btn = document.querySelector('button');
            btn.addEventListener('click', function () {
                alert(11);
            })
        })
        img.addEventListener('load', function () {
            //等待图片加载完毕后再执行里面的代码 
        })
```

![image-20230511201033392](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109113.png)

```
// HTML文档加载完后便执行加载速度更快
        document.addEventListener('DOMContentLoaded', function () {
            const btn = document.querySelector('button');
            btn.addEventListener('click', function () {
                alert(11);
            })
        })
```

> **页面加载事件有哪两个?如何添加?**

#### **load 事件**

> **监听整个页面资源给window 加**

#### **DOMContentLoaded**

> **给document加**
> **无需等待样式表、图像等完全加载**

![image-20230511201655133](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109114.png)

### 页面滚动事件

![image-20230511202737396](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109115.png)

![image-20230511204604708](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109116.png)

```
 const div = document.querySelector('div');
        div.addEventListener('scroll', function () {
            // 获取元素被卷去的头部大小
            console.log(div.scrollTop);
        })
```

![image-20230511205837812](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109117.png)

![image-20230511205811279](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109118.png)

```
// scrollTop可读写
        document.documentElement.scrollTop = 1000;

// 返回顶部的两种方法
      // document.documentElement.scrollTop = 0;
      // window.scrollTo(x,y)
      window.scrollTo(0, 0);
```

![image-20230512084755925](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109119.png)





### 页面尺寸事件 -resize

![image-20230512100939002](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109120.png)

#### clientWidth获取元素宽高

**(不包含边框 margin 滚动条)**

![image-20230512101605744](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109121.png)

#### offset家族

**(获取元素的自身宽高、包含元素自身设置的宽高、padding、border)**

**(还可以获取元素的位置)**

**(它们都是只读属性)**

![image-20230512103600930](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109122.png)

![image-20230512100904413](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109123.png)

#### element.getBoundingClientRect()方法返回元素的大小及其相对于视口的位置

![image-20230512160017025](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109124.png)

|              属性              |                     作用                     |                            说明                            |
| :----------------------------: | :------------------------------------------: | :--------------------------------------------------------: |
|   **scrollLeft和scrollTop**    |            **被卷去的头部和左侧**            |                **配合页面滚动来用，可读写**                |
| **clientWidth 和clientHeight** |            **获得元素宽度和高度**            | **不包含border,margin，滚动条用于js获取元素大小,只读属性** |
| **offsetWidth和offsetHeight**  |            **获得元素宽度和高度**            |         ==**包含border、paaaing,滚动条等，只读**==         |
| **==offsetLeft和offsetTop==**  | **获取元素距离自己定位父级元素的左、上距离** |          ==**获取元素位置的时候使用，只读属性**==          |

### 电梯导航案例

![image-20230512162421781](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109125.png)

![image-20230512205211831](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305122109126.png)

### 日期对象

![image-20230513163443304](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614279.png)

#### 日期对象方法

![image-20230513163808684](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614281.png)

### 时间戳

![image-20230513184442595](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614282.png)

#### 获取时间戳

![image-20230513185615849](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614283.png)

```
 const date = new Date()
        //1. date.getTime()
        console.log(date.getTime());
        // 2. +new Date()
        console.log(+new Date());
        // 3. Date.now()
        console.log(Date.now());
```

### DOM节点

![image-20230514093252430](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614284.png)

#### 查找节点

![image-20230514093704017](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614285.png)

##### 父节点查找

![image-20230514100031710](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614286.png)

##### 子节点查找

![image-20230514104615153](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614287.png)

**兄弟关系查找**

![image-20230514104749644](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614288.png)

```
     <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
        <li>5</li>
    </ul>
    <script>
        const li2 = document.querySelector('ul li:nth-child(2)')
        const ul = document.querySelector('ul')
        // 查找子节点 获取的是一个伪数组
        console.log(ul.children)
        // 查找上一个兄弟节点
        console.log(li2.previousElementSibling)
        // 查找下一个兄弟节点
        console.log(li2.nextElementSibling)
    </script>
```

#### 增加节点

![image-20230514152117558](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614289.png)

##### 创建节点

![image-20230514152143800](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614290.png)

##### 追加节点

![image-20230514153439710](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614291.png)

```
const ul = document.querySelector('ul')
        // 创建节点
        const div = document.createElement('div')
        // 追加节点 
        // 插入到这个父元素的最后
        // 父元素.appendchild(要插入的元素)
        // document.body.appendChild(div)
        //插入到某个子元素的前面
        // 插入到某个子元素的前面
        // 父元素.insertBefore(要插入的元素,在哪个元素前面)
        ul.insertBefore(div, ul.children[0])
        div.innerHTML = '周杰伦'
```

## 4.DOM

### 学成在线渲染案例

![image-20230514160651152](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614292.png)

### 克隆节点

![image-20230514160935442](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614293.png)

```
const ul = document.querySelector('ul')
        // 克隆节点
        const li1 = ul.children[0].cloneNode(true)
        // const li1 = ul.children[0].cloneNode()
        ul.appendChild(li1)
```



### 删除节点

![image-20230514162923812](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614294.png)

```
 const ul = document.querySelector('ul')
        // 父元素.removeChild(加要删除的元素)
        ul.removeChild(ul.children[0])
```

### M端事件

![image-20230514163805381](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614295.png)

### 学生信息表案例

![image-20230516101430872](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614296.png)

![image-20230516101454851](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614297.png)

![image-20230516101513412](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614298.png)

![image-20230516101533407](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614299.png)

![image-20230514204507089](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614300.png)

![image-20230516100111275](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614301.png)

## 1.BOM

**BOM(Browser Object Model）是浏览器对象模型**

![image-20230516103803074](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614302.png)

<ul><li>
    window对象是一个全局对象，也可以说是JavaScript中的顶级对象</li>
    <li>像document、alert()、console.log()这些都是window的属性</li>
    <li>基本BOM的属性和方法都是window所有通过var定义在全局作用域中的变量、函数都会变成window对象的属性和方法
</li>
    <li>window对象下的属性和方法调用的时候可以省略window</li></ul>



### 延时函数

![image-20230517194452252](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614303.png)

![image-20230517200806316](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614304.png)

### JS执行机制

为了解决这个问题，利用多核CPU的计算能力，HTML5提出Web Worker标准，允许JavaScript脚本创建多个线程。于是，JS 中出现了同步和异步。

#### **同步**

前一个任务结束后再执行后一个任务，程序的执行顺序与任务的排列顺序是一致的、同步的。比如做饭的同步做法:我们要烧水煮饭，等水开了(10分钟之后)，再去切菜，炒菜。

#### **异步**

你在做一件事情时，因为这件事情会花费很长时间，在做这件事的同时，你还可以去处理其他事情。比如做饭的异步做法，我们在烧水的同时，利用这10分钟，去切菜，炒菜。

![image-20230517203102216](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614305.png)

#### 事件循环

![image-20230517204638573](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614307.png)

### location对象

location的数据类型是对象，它拆分并保存了URL地址的各个组成部分

![image-20230518092052279](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614308.png)

跳转页面 href属性

```
// 跳转页面
                location.href = "https://www.bilibili.com"
```

search属性获取地址中携带的参数,符号?后面部分

![image-20230518092419176](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614309.png)

```
<!-- search属性 -->
    <form action="">
        文本：<input type="text" name="text">
        密码：<input type="password" name="pwd">
        <button type="submit">提交</button>
    </form>
    <!-- JS_practice/location%E5%AF%B9%E8%B1%A1.html?text=pink&pwd=123456 -->
```

hash属性获取地址中的哈希值，符号#后面部分

后期vue路由的铺垫，经常用于不刷新页面，显示不同页面，比如网易云音乐

![image-20230518093620047](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614310.png)

reload方法用来刷新当前页面，传入参数true时表示强制刷新

![image-20230518093951125](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614311.png)

```
  const btn = document.querySelector('button')
        btn.addEventListener('click', function () {
            // 相当于 F5刷新
            location.reload()
            // 相当于 ctrl+F5强制刷新
            location.reload(true)
        })
```

![image-20230518100115433](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614312.png)

### navigator对象

![image-20230518103925539](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614313.png)

```
// 检测 userAgent（浏览器信息）
    !(function () {
      const userAgent = navigator.userAgent
      // 验证是否为Android或iPhone
      const android = userAgent.match(/(Android);?[\s\/]+([\d.]+)?/)
      const iphone = userAgent.match(/(iPhone\sOS)\s([\d_]+)/)
      // 如果是Android或iPhone，则跳转至移动站点
      if (android || iphone) {
        location.href = 'http://m.itcast.cn'
      }
    })();
```

### history对象

history的数据类型是对象，主要管理历史记录，该对象与浏览器地址栏的操作相对应，如前进、后退、历史记录等

![image-20230518104924608](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614314.png)

### 本地存储分类-localStorage

![image-20230518200856469](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614315.png)

LocalStorage的使用

可以将数据永久存储在本地（用户的电脑），除非手动删除，否则关闭页面也会存在

![image-20230518203207571](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614316.png)

![image-20230518203919054](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614317.png)

本地存储分类-sessionStorage

生命周期为关闭浏览器窗口

![image-20230518205740079](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614318.png)

### 本地存储复杂数据类型

需要将复杂数据类型转换成JS0N字符串，在存储到本地

![image-20230519092617357](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614319.png)

因为本地存储里面取出来的是字符串，不是对象，无法直接使用

![image-20230519092755748](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614320.png)

把取出来的字符串转换为对象来使用

![image-20230519092830984](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614321.png)

### 学生就业统计表案例

![image-20230519160516126](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614322.png)

#### 渲染业务

![image-20230519160810063](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614323.png)

![image-20230519202025282](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614324.png)

数组map方法 数组join方法

![image-20230519203105910](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614325.png)

```
 		// 1.map()方法
        // arr = ['pink', 'Jay', 'David', '周杰伦'];
        // const new_arr = arr.map(function (ele, index) {
        //     // console.log(ele);//元素
        //     // console.log(index);//索引号
        //     return ele + "YYDS";
        // });
        // console.log(new_arr);
        // 2.join()方法
        arr = ['pink', 'Jay', 'David', '周杰伦'];
        console.log(arr.join());//结果为 pink,Jay,David,周杰伦
        console.log(arr.join(''));//结果为pinkJayDavid周杰伦
        console.log(arr.join('和'));//结果为pink和Jay和David和周杰伦
        console.log(arr.join('|'));//结果为pink|Jay|David|周杰伦
```

#### 新增业务

![image-20230520084222306](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614326.png)

![image-20230520160314623](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614327.png)

#### 删除业务

![image-20230520162832257](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614328.png)

关于stuld的处理

![image-20230520164921784](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614329.png)

### 正则表达式

![image-20230520171252172](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614330.png)

●正则表达式在JavaScript中的使用场景：
>例如验证表单：用户名表单只能输入英文字母、数字或者下划线，昵称输入框中可以输入中文（匹配）
>比如用户名：/[a-z0-9-]{3,16}$/
>过滤掉页面内容中的一些敏感词（替换），或从字符串中获取我们想要的特定部分（提取）等。

![image-20230520171513012](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614331.png)

#### 语法

正则同样道理，我们分为两步：先定义规则
再查找

![image-20230520172306152](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614332.png)



![image-20230520192134980](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614333.png)

test()方法用来查看正则表达式与指定的字符串是否匹配

![image-20230520193710094](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614334.png)

#### 元字符

元字符（特殊字符）
是一些具有特殊含义的字符，可以极大提高了灵活性和强大的匹配功能。

>比如，规定用户只能输入英文26个英文字母，普通字符的话abcdefghijklm.…
>但是换成元字符写法：[a-z]

![image-20230520194945379](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614335.png)

<ul>
    <li>元字符进行了分类：</li>
    <li>    边界符（表示位置，开头和结尾，必须用什么开头，用什么结尾）</li>
    <li>量词（表示重复次数）</li>
    <li>字符类（比如\d表示0~9）</li>

![image-20230520195358859](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614336.png)

##### 边界符

![image-20230520201117415](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614337.png)

##### 量词

![image-20230520205216644](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614338.png)

```
 // const arr = 'web前端开发';
        // const reg = /web/;
        // // 检测是否匹配
        // console.log(reg.test(arr));
        // // 获取匹配项
        // console.log(reg.exec(arr));//获取匹配项返回一个数组
        // console.log('--------------------');
        // //元字符
        //1.边界符
        console.log(/^二哈/.test("二哈"));//true
        console.log(/^二哈/.test("二哈二哈"));//true
        console.log(/^二哈$/.test('二哈'));//true
        console.log(/^二哈$/.test('二哈二哈'));//false
        console.log('------------------------------------');
        // 2.量词
        // * 出现 >=0 次
        console.log(/^哈*$/.test('二哈'));//flase
        console.log(/^哈*$/.test(''));//true
        console.log(/^哈*$/.test('哈'));//true
        console.log(/^哈*$/.test('哈哈'));//true
        console.log(/^哈*$/.test('哈哈哈'));//true
        console.log(/^哈*$/.test('哈哈哈哈'));//true
        console.log(/^哈*$/.test('哈哈哈哈哈'));//true
        console.log('-------------------------------');
        // + 重复出现 >=1 次
        console.log(/^哈+$/.test('二哈'));//flase
        console.log(/^哈+$/.test(''));//flase
        console.log(/^哈+$/.test('哈'));//true
        console.log(/^哈+$/.test('哈哈'));//true
        console.log(/^哈+$/.test('哈哈哈'));//true
        console.log(/^哈+$/.test('哈哈哈哈'));//true
        console.log(/^哈+$/.test('哈哈哈哈哈'));//true
        console.log('-------------------------------');
        // ? 出现 1 || 0
        console.log(/^哈?$/.test('二哈'));//flase
        console.log(/^哈?$/.test(''));//true
        console.log(/^哈?$/.test('哈'));//true
        console.log(/^哈?$/.test('哈哈'));//flase
        console.log(/^哈?$/.test('哈哈哈'));//flase
        console.log(/^哈?$/.test('哈哈哈哈'));//flase
        console.log(/^哈?$/.test('哈哈哈哈哈'));//flase
```

##### 字符类

![image-20230521093531677](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614339.png)

![image-20230521093151645](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614340.png)

![image-20230521093238352](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614341.png)

![image-20230521093324588](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614342.png)

(2) . 匹配除换行符之外的任何单个字符

![image-20230521102049058](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614343.png)

#### 修饰符

![image-20230521143549076](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614344.png)

替换replace替换

![image-20230521144113712](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614345.png)

## 2.BOM

### 小兔鲜儿页面注册

![image-20230521161259471](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305211614346.png) 

![image-20230522084748698](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202308291014807.png)

![image-20230522084332670](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202308291014808.png)

### 小兔鲜登录页面

![image-20230522102645925](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202308291014809.png)

![image-20230522102720054](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202308291014810.png)

# 个人实战文档

本次实战是对自己整个api阶段的总结。

参考效果如下地址：

http://erabbit.itheima.net/#/product/3995139

本次实战主要分为以下几个模块。

## 顶部导航模块

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202308291014811.gif">

需求：

1. 顶部导航开始不显示
2. 等页面滑到主导航栏，这个**新顶部导航栏滑动下拉显示**，并且改为固定定位
3. 等页面滑到上面，新顶部导航栏隐藏

## 图片切换模块

 <img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202308291014812.gif">



## 放大镜效果

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202308291014813.gif">



业务分析：

①：鼠标经过对应小盒子，左侧中等盒子显示对应中等图片

②： 鼠标经过中盒子，右侧会显示放大镜效果的大盒子

③： 黑色遮罩盒子跟着鼠标来移动

④： 鼠标在中等盒子上移动，大盒子的图片跟着显示对应位置





思路分析：

①：鼠标经过小盒子，左侧中等盒子显示对应中等图片

1. 获取对应的元素
2. 采取事件委托的形式，监听鼠标经过小盒子里面的图片， 注意此时需要使用 `mouseover` 事件，因为需要事件冒泡触发small 
3. 让鼠标经过小图片的爸爸li盒子，添加类，其余的li移除类（注意先移除，后添加）
4. 鼠标经过小图片，可以拿到小图片的src， 可以做两件事
   - 让中等盒子的图片换成这个 这个小图片的src
   - 让大盒子的背景图片，也换成这个小图片的 src （稍后做）





②： 鼠标经过中等盒子，右侧大盒子显示

1. 用到鼠标经过和离开，鼠标经过中盒子，大盒子 利用 display 来显示和隐藏

2. 鼠标离开不会立马消失，而是有200ms的延时，用户体验更好，所以尽量使用定时器做个延时 setTimeout

3. 显示和隐藏也尽量定义一个函数，因为鼠标经过离开中等盒子，会显示隐藏，同时，**鼠标经过大盒子，也会显示和隐藏**

4. 给大盒子里面的背景图片一个默认的第一张图片

   

③： 黑色遮罩盒子跟着鼠标来移动

1.  先做鼠标经过 中等盒子，显示隐藏 黑色遮罩 的盒子

2.  让黑色遮罩跟着鼠标来走, 需要用到鼠标移动事件  mousemove  

3. 让黑色盒子的移动的核心思想：不断把鼠标在中等盒子内的坐标给黑色遮罩层 let  top 值，这样遮罩层就可以跟着移动了

   - 需求

     - 我们要的是 鼠标在 中等盒子内的坐标， 没有办法直接得到
     - 得到1：  鼠标在页面中的坐标
     - 得到2：  中等盒子在页面中的坐标

   - 算法

     - 得到鼠标在页面中的坐标    利用事件对象的  pageX  
     - 得到middle中等盒子在页面中的坐标   middle.getBoundingClientRect()
     - 鼠标在middle 盒子里面的坐标   =   鼠标在页面中的坐标  -   middle 中等盒子的坐标
     - 黑色遮罩层不断得到       鼠标在middle 盒子中的坐标 就可以移动起来了

     >注意 y坐标特殊，需要减去 页面被卷去的头部 
     >
     >为什么不用 box.offsetLet 和 box.offsetTop  因为这俩属性跟带有定位的父级有关系，很容被父级影响，而getBoundingClientRect() 不受定位的父元素的影响

   - 限定遮罩的盒子只能在middle 内部移动，需要添加判断

     - 限定水平方向 大于等于0 并且小于等于 400
     - 限定垂直方向 大于等于0 并且小于等于 400

   - 遮罩盒子移动的坐标： 

     - 声明一个 mx 作为移动的距离
     - 水平坐标 x 如果 小于等于100 ，则移动的距离 mx 就是  0  不应该移动
     - 水平坐标 如果 大于等于100 并且小于300，移动的距离就是  mx - 100 （100是遮罩盒子自身宽度的一半）
     - 水平坐标 如果 大于等于300，移动的距离就是  mx   就是200  不应该在移动了
     - 其实我们发现水平移动， 就在 100 ~ 200 之间移动的
     - 垂直同理

   ~~~javascript
   let mx = 0, my = 0;
   if (x <= 100) mx = 0
   if (x > 100 && x < 300) mx = x - 100
   if (x >= 300) mx = 200
   
   if (y <= 100) my = 0
   if (y > 100 && y < 300) my = y - 100
   if (y >= 300) my = 200
   ~~~

   - 大盒子图片移动的计算方法：
     - 中等盒子是 400px  大盒子 是 800px 的图片
     - 中等盒子移动1px， 大盒子就应该移动2px， 只不过是负值

   ~~~JavaScript
   large.style.backgroundPositionX = - 2 * mx + 'px'
   large.style.backgroundPositionY = - 2 * my + 'px'
   ~~~

   放大镜完整代码：

   






## 其他模块

此模块可以根据自己时间添加

### 点击模块

 <img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202308291014814.gif">

### tab栏切换模块

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202308291014815.gif">



### 返回顶部模块

页面滚动底部，可以出现一个侧边栏，点击返回顶部，可以返回顶部
