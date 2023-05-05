# JS基础-ECMAScript

## 对象

### 使用原型(prototype)创建对象

当我们创建一个函数时，函数就会自动拥有一个`prototype`属性，这个属性的值是一个对象，这个对象被称为该函数的原型对象。也可以叫做原型。

```
function Store() {};
Store.prototype.name = "SF Express";
Store.prototype.locaion = "Hong Kong";
Store.prototype.salesVolume = 1200000000;
// 创建对象
var myStore = new Store();
// 创建一个新的对象
var hisStore = new Store();
hisStore.name = "STO Express";    // 覆盖了原来的name属性
```

### 属性的检测

属性的检测指检查对象是否有某个属性或者方法，需要使用运算符`in`，`in`的左侧是属性或者方法名，右侧是检查对象，对象有该属性或者方法则返回

```
var school = {
    name:"SJTU",
    location:"ShangHai",
    studentNum:40000,
    display:function() {
          console.log(this.name);
    }
};
// 检测属性
console.log("name" in school);    // 输出true
console.log("sales" in school);    // 输出false
// 检测方法
console.log("display" in school);    // 输出true
console.log("print" in school);    // 输出false
```

`true`，否则返回`false`

### Date对象

```
展示了用来创建一个日期对象的多种方法
var today = new Date();
var birthday = new Date('December 17, 1995 03:24:00');
var birthday = new Date('1995-12-17T03:24:00');
var birthday = new Date(1995, 11, 17);
var birthday = new Date(1995, 11, 17, 3, 24, 0);
```

### 内置对象

#### Math对象

##### Math对象生成随机数

```
// 生成一个0到10的随机数
        let getRandom = Math.floor(Math.random() * 11);
        // 生成一个3到10的随机数
        // let b = Math.floor(Math.random() * (10 - 3 + 1) + 3);
        let b = Math.floor(Math.random() * (10 - 3 + 1)) + 3;
        // 生成一个N到M的随机数
        // let c = Math.floor(Math.random() * (M - N + 1) + N);
        // let c = Math.floor(Math.random() * (M - N + 1) ) + N;
        console.log(b);
```

![image-20230425201045707](./Typora-image/image-20230425201045707.png)

![image-20230427191540227](./Typora-image/image-20230427191540227.png)**

### 数据类型

**==值类型== 存储的值的本身**

**==引用类型== 存储的仅是地址**

![image-20230427191324737](./Typora-image/image-20230427191324737.png)

#### 堆和栈

**引用数据类型的值实际存储在堆中**

<img src="./Typora-image/image-20230427192643306.png" alt="image-20230427192643306" style="zoom:50%;" />

<img src="./Typora-image/image-20230427192357053.png" alt="image-20230427192357053" style="zoom: 67%;" />

# Web-APIs

## 变量的声明

**const优先**

![image-20230427195002528](./Typora-image/image-20230427195002528.png)

![image-20230427195157917](./Typora-image/image-20230427195157917.png)

![image-20230427195245263](./Typora-image/image-20230427195245263.png)

![image-20230427200004351](./Typora-image/image-20230427200004351.png)

![image-20230427200108843](./Typora-image/image-20230427200108843.png)

![image-20230427200220579](./Typora-image/image-20230427200220579.png)

## 总结 

**数组和对象建议用const来声明**

![image-20230427200418132](./Typora-image/image-20230427200418132.png)

## DOM

![image-20230427200848938](./Typora-image/image-20230427200848938.png)![image-20230427201037564](./Typora-image/image-20230427201037564.png)

**DOM树**

![image-20230427201502191](./Typora-image/image-20230427201502191.png)

### DOM对象

![image-20230427202133682](./Typora-image/image-20230427202133682.png)·

```
 //浏览器根据HTML标签自动生成了DOM对象
        // 显示选中的第一个标签 query查询 Selector选择器
        let div = document.querySelector('div');
        // 在控制台显示DOM对象
        console.dir(div);
```

![image-20230427202744993](./Typora-image/image-20230427202744993.png)

### ==获取DOM元素==

****



**根据CSS选择器来获取DOM元素**

![image-20230427204059406](./Typora-image/image-20230427204059406.png)

![image-20230428080757607](./Typora-image/image-20230428080757607.png)

**修改元素内容·**

![image-20230428081204437](./Typora-image/image-20230428081204437.png)

```js
// 获取元素
        const box = document.querySelector('.box');
        // 修改元素内容
        // box.innerText = '我是盒子'//修改文字内容
        // console.log(box.innerText);//获取文字内容
        // box.innerText = '<b>我是盒子</b>';//innerText 不能解析HTML标签元素
        // box.innerHTML = '<b>我是盒子</b> '//innerHTML可以解析HTML标签元素
```

### 操作元素常用属性

```js
const img = document.querySelector('img');
        img.src = './images/2.webp';
        img.title = 'pink老师的艺术照'
```

![image-20230502202551414](./Typora-image/image-20230502202551414.png)

### 操作元素样式属性

**小驼峰命名法**

![image-20230502203623441](./Typora-image/image-20230502203623441.png)

### 操作类名来操作css

![image-20230503194237763](./Typora-image/image-20230503194237763.png)

![image-20230503194814954](./Typora-image/image-20230503194814954.png)

```
// 获取元素
        const div = document.querySelector('div');
        // 添加类名
        div.className = 'box nav';
```

![image-20230503195950760](./Typora-image/image-20230503195950760.png)

### ==通过classlist修改样式==

![image-20230503202229617](./Typora-image/image-20230503202229617.png)

![image-20230503202056926](./Typora-image/image-20230503202056926.png)

```
 const div = document.querySelector('div');
        // 追加类add()
        // div.classList.add('nav');
        //删除类名
        // div.classList.remove('box');
        // 切换类toggle 有则删除无则添加
        // div.classList.toggle('box');
        div.classList.toggle('nav');
```

![image-20230503202443783](./Typora-image/image-20230503202443783.png)

### 随机轮播图

```
/* 生成随机数 */
    const random = Math.floor(Math.random() * sliderData.length);
    /* 1.获取图片元素 */
    const img = document.querySelector('.slider-wrapper img');
    img.src = sliderData[random].url;
    /*  2.获取标题元素 */
    const p = document.querySelector('.slider-footer p');
    p.innerHTML = sliderData[random].title;
    /* 3.获取slider-footer元素 */
    const footer = document.querySelector('.slider-footer');
    /* 修改背景颜色 */
    footer.style.backgroundColor = sliderData[random].color;
    /* 获取对应的小圆点 */
    const li = document.querySelector(`.slider ul li:nth-child(${random + 1})`);
    /* 为获取的li添加active 类名 */
    li.classList.add('active');
```

### 操作表单元素的属性

![image-20230505084331648](./Typora-image/image-20230505084331648.png)

![image-20230505084215500](./Typora-image/image-20230505084215500.png)
