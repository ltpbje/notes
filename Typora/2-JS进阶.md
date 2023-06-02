# JS进阶

## 作用域

![image-20230524204746256](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305252055821.png)

### 局部作用域

局部作用域分为函数作用域和块作用域。

#### 函数作用域

![image-20230524211200958](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305252055823.png)

#### 块作用域

![image-20230524211257747](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305252055825.png)

### 全局作用域

![image-20230524211357729](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305252055826.png)

### 总结

1.全局作用域有哪些？

<script>标签内部
js文件

2.全局作用域声明的变量其他作用域能使用吗？
相当能
JavaScript中的作用域是程序被执行时的底层机制，了解这一机制有
助于规范代码书写习惯，避免因作用域导致的语法错误。

### 作用域链

作用域链本质上是底层的变量查找机制。

> 在函数被执行时，会优先查找当前函数作用域中查找变量
>
> 如果当前作用域查找不到则会依次逐级查找父级作用域直到全局作用域

![image-20230525094702289](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305252055827.png)

### JS垃圾回收机制

![image-20230525095503080](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305252055828.png)

内存的生命周期

![image-20230525095035049](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305252055829.png)

总结

![image-20230525095332986](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305252055830.png)

拓展JS垃圾回收机制-算法说明

![image-20230525095620705](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305252055831.png)

引用计数法

IE采用的引用计数算法，定义“内存不再使用”，就是看一个对象是否有指向它的引用，没有引用了就回收对象
算法：

1.跟踪记录被引用的次数
2.如果被引用了一次，那么就记录次数1，多次引用会累加++
3.如果减少一个引用就减1

4.如果引用次数是0，则释放内存

但它却存在一个致命的问题：嵌套用（循环引用）
如果两个对象相互引用，尽管他们已不再使用，垃圾回收器不会进行回收，导致内存泄露

![image-20230525100607588](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305252055832.png)

标记清除法

![image-20230525100908117](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305252055833.png)

标记清除法原理

![image-20230525100929812](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305252055835.png)

![image-20230525171523588](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305252055836.png)

### ==闭包==

简单理解：闭包=内层函数+外层函数的变量

可以在内层函数中访问到其外层函数的作用域

![image-20230525171706546](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305252055837.png)

闭包作用：封闭数据，提供操作，外部也可以访问函数内部的变量

闭包的基本格式：

![image-20230525171939499](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305252055838.png)

>==总结==
>
>1.怎么理解闭包？
>
>闭包=内层函数+外层函数的变量
>2.闭包的作用？
>封闭数据，实现数据私有，外部也可以访问函数内部的变量
>闭包很有用，因为它允许将函数与其所操作的某些数据（环境）关联起来
>3.闭包可能引起的问题？
>内存泄漏

### 变量提升

它允许在变量声明之前即被访问（仅存在于var声明变量）

![image-20230525175117130](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305252055839.png)

日标：了解什么是变量提升
说明：JS初学者经常花很多时间才能习惯变量提升，还经常出现一些意想不到的bug,正因为如此，ES6引入了块级作用域，用1et或者const声明变量，让代码写法更加规范和人性化。

总结

>1.用哪个关键字声明变量会有变量提升？ var
>2.变量提升是什么流程？
>==先把Var变量提升到当前作用域于最前面
>只提升变量声明，不提升变量赋值==
>然后依次执行代码
>我们不建议使用var声明变量

## 函数进阶

### 函数提升

函数提升与变量提升比较类似，是==指函数在声明之前即可被调用==。

函数表达式不存在提升的现象

函数提升出现在相同作用域当中最前面的位置

![image-20230525190856909](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305252055840.png)

### 函数参数

函数参数的使用细节，能够提升函数应用的灵活度。
学习路径：1.动态参数2.剩余参数

#### 动态参数

arguments是函数内部内置的==伪数组变量==，它包含了调用函数时传入的所有实参

arguments是一个伪数组，只存在于函数中

![image-20230525200140571](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305252055841.png)

>1.当不确定传递多少个实参的时候，我们怎么办？ arguments动态参数
>2.arguments是什么？ 伪数组 它只存在函数中

`arguments`对象不是一个 [`Array`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array) 。它类似于`Array`，但除了 length 属性和索引元素之外没有任何`Array`属性。例如，它没有 [pop](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/pop) 方法。但是它可以被转换为一个真正的`Array`：

#### 剩余参数

新定义的函数会覆盖原来定义的函数

目标：能够使用剩余参数
剩余参数允许我们将一个不定数量的参数表示为一个==数组==

得到的是一个真数组

```
 //剩余参数 
        function getSum(...arr) {
            console.log(arr);
            // console.log(sum);
        };
```

开发中，还是提倡多使用剩余参数。

>==总结==
>
>1.剩余参数主要的使用场景是？用于获取多余的实参
>2.剩余参数和动态参数区别是什么？开发中提倡使用哪一个？动态参数是伪数组剩余参数是真数组
>开发中使用刺余参数想必也是极好的

### 展开运算符

展开运算符和剩余参数  一个在函数外使用  一个在函数内使用

![image-20230525203330029](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202305252055842.png)

### 展开运算符or剩余参数

剩余参数：函数参数使用，得到==真数组==
展开运算符：数组中使用，数组展开



### ==箭头函数(重要)==

![image-20230528103411816](./Typora-image/image-20230528103411816.png)

#### 语法

##### 语法1：基本写法

![image-20230528150034661](./Typora-image/image-20230528150034661.png)

##### 语法2：只有一个参数可以省略小括号

![image-20230528150304075](./Typora-image/image-20230528150304075.png)

##### 语法3：如果函数体只有一行代码，可以写到一行上，并且无需写return直接返回值

![image-20230528150142170](./Typora-image/image-20230528150142170.png)

##### 语法4：加括号的函数体返回对象字面量表达式

![image-20230528151931050](./Typora-image/image-20230528151931050.png)

#### 箭头函数参数

1.普通函数有arguments动态参数
2.箭头函数没有arguments动态参数，但是有剩余参数...args

箭头函数里面有arguments:动态参数吗？可以使用什么参数？

>没有arguments动态参数
>可以使用剩余参数

#### 箭头函数this

箭头函数不会创建自己的this,它只会从自己的作用域链的上一层沿用this。

![image-20230528154014105](./Typora-image/image-20230528154014105.png)

在开发中【使用箭头函数前需要考虑函数中this的值】，事件回调函数使用箭头函数时，this为全局的window,因此
==DOM事件回调函数为了简便，还是不太推荐使用箭头函数==

```
// // 语法1.基本写法
        // const fn1 = () => {
        //     console.log('我是箭头函数');
        // };
        // fn1();
        // //语法2. 只有一个参数可以省略小括号
        // const fn2 = x => {
        //     return x + x;
        // };
        // console.log(fn2(2));
        // //语法3. 如果函数体只有一行代码，可以写到一行上，并且无需写return直接返回值
        // const fn3 = (x, y) => x + y;
        // console.log(fn3(1, 2));
        // // 语法4：加括号的函数体返回对象字面量表达式
        // const fn4 = uname => ({ uname: uname });
        // console.log(fn4('pink老师'));
        // 箭头函数 不会自己创建 this 只会从自己的作用域链的上一层沿用this。
        // const fn1 = () => this;
        // console.log(fn1());//window
        function outer() {
            const fn2 = () => console.log(this);
            fn2();
        };
        // window.outer window调用的outer所以this指向window
        console.log(outer());//window
```

总结

![image-20230528154855924](./Typora-image/image-20230528154855924.png)

# 解构赋值

目标：知道解构的语法及分类，使用解构简洁语法快速为变量赋值

**左侧**的 [ ] 用于批量声明变量    **右侧**数组的单元值将被赋值给左侧的变量

## 数组解构

![image-20230528170416124](./Typora-image/image-20230528170416124.png)

```
// // 变量少，单元值多
        // const [a, b, c] = ['小米', '苹果', '华为', '格力'];
        // console.log(a);//小米
        // console.log(b); //苹果
        // console.log(c); //华为
        // 利用剩余参数变量少，单元值多
        // const [a, b, ...tel] = ['小米', '苹果', '华为', '格力', 'vivo'];
        // console.log(a);//小米
        // console.log(b);//苹果
        // console.log(tel);//['华为', '格力', 'vivo']
        // // 防止有undefined传递单元值的情况，可以设置默认值：
        // const [a = '手机', b = '华为'] = ['小米'];
        // console.log(a);//小米
        // console.log(b);//华为
        // // 按需导入，忽略某些值
        // const [a, , c, d] = ['小米', '苹果', '华为', '格力', 'vivo'];
        // console.log(a);//小米
        // console.log(c);//华为
        // console.log(d);//格力
        // //支持多维数组的解构
        // const [a, b] = ['苹果', ['小米', '华为']];
        // console.log(a);//苹果
        // console.log(b);//['小米','华为']
        const [a, [b, c]] = ['苹果', ['小米', '华为']];
        console.log(a);//苹果
        console.log(b);//小米
        console.log(c);//华为

```

![image-20230529083636432](./Typora-image/image-20230529083636432.png)

1.变量的数量大于单元值数量时，多余的变量将被赋值为？
undefined
2.变量的数量小于单元值数量时，可以通过什么剩余获取所有的值？

剩余参数...获取剩余单元值，但只能置于最末位

## 对象解构

对象解构是将对象属性和方法快速批量赋值给一系列变量的简洁语法

### 基本语法：

1.赋值运算符=左侧的 {  } 用于批量声明变量，右侧对象的属性值将被赋值给左侧的变量

2.对象属性的值将被赋值给与==属性名相同的变量==

3.注意解构的变量名不要和外面的变量名冲突否则报错

4.对象中找不到与变量名一致的属性时变量值为undefined

### 给新的变量名赋值用 ：

可以从一个对象中提取变量并同时修改新的变量名

```
 // const pig = { name: '佩奇', age: 6 };
        // const { name: uname, age } = pig;
        // console.log(uname);//佩奇
        // console.log(age);//6
```

冒号表示“什么值 : 赋值给谁”

### 数组对象解构

```
const [{ goodsName, price }] = goods;
        console.log(goodsName);//小米
        console.log(price);//1999
```

### 多级对象解构

![image-20230529094227417](./Typora-image/image-20230529094227417.png)

```
  // 需求1： 请将以上msg对象  采用对象解构的方式 只选出  data 方面后面使用渲染页面
    const { data } = msg;
    console.log(data);
 // 需求2： 上面msg是后台传递过来的数据，我们需要把data选出当做参数传递给 函数

    function render({ data }) {
      // 我们只要 data 数据
      // 内部处理
      console.log(data);
    }
    render(msg)
     // 需求3， 为了防止msg里面的data名字混淆，要求渲染函数里面的数据名改为 myData
    function render({ data: myData }) {
      // 要求将 获取过来的 data数据 更名为 myData
      // 内部处理
      console.log(myData);
    }
```

## ==遍历数组forEach方法（重点）==

foreach( )没有返回值

![image-20230530100641994](./Typora-image/image-20230530100641994.png)

```
 const arr = ['小米', '华为', 'vivo'];
        //forEach()不会像map()方法那样返回数组
        const a = arr.forEach((item, index) => {
            console.log(item);//数组中的元素
            console.log(index);//索引号
        });
        console.log(a);//undefined
```

![image-20230530100746717](./Typora-image/image-20230530100746717.png)

## filter ( )筛选过滤数组方法

```
 const arr = [100, 200, 300, 10, 2];
        // 筛选大于等于200的元素
        const newArr = arr.filter(item => item >= 200);
        console.log(newArr);// [200,300]
```

![image-20230530202119844](./Typora-image/image-20230530202119844.png)

1) 筛选数组

2) 返回值：返回数组，包含了符合条件的所有元素。如果没有符合条件的元素则返回空数组

3) 参数：currentValue必须写，index可选

4) ## 因为返回新数组，所以不会影响原数组



# 深入对象

## 创建对象三种方式

![image-20230531203708393](./Typora-image/image-20230531203708393.png)

![image-20230531203740422](./Typora-image/image-20230531203740422.png)

构造函数在技术上是常规函数。 不过有两个约定： 1. 它们的命名以大写字母开头。 2. 它们只能由 "new" 操作符来执行。

## 构造函数实例化执行过程

1) 利用new创建新的空对象
2) this指向新的对象
3) 执行构造函数代码,添加新的属性
4) 返回新的对象



![image-20230531210251959](./Typora-image/image-20230531210251959.png)

## 实例成员

![image-20230601091655978](./Typora-image/image-20230601091655978.png)

## 静态成员

![image-20230601091736243](./Typora-image/image-20230601091736243.png)

![image-20230601091810605](./Typora-image/image-20230601091810605.png)

## 内置构造函数

![image-20230601094142342](./Typora-image/image-20230601094142342.png)

引用类型

Object,Array,RegExp,Date

包装类型

String,Number,Boolean

### Object

![image-20230601095456370](./Typora-image/image-20230601095456370.png)

#### 三个常用静态方法（静态方法就是只有构造函数0 bject可以调用的）

作用：Object.keys静态方法获取对象中所有属性 (键)

```
 const person = { name: 'pink', age: 18 };
 console.log(Object.keys(person));//['name', 'age']
```

作用：Object..values静态方法获取对象中所有属性值 (值)

```
console.log(Object.values(person));//['pink', 18]
```

作用：Object. assign 静态方法常用于对象拷贝

```
const o = {};
console.log(Object.assign(o, person));//{name: 'pink', age: 18}
```

使用：经常使用的场景给对象添加属性

```
Object.assign(o, { gender: '女' });
console.log(o);//{name: 'pink', age: 18, gender: '女'}
```

![image-20230601100835127](./Typora-image/image-20230601100835127.png)

### Array

forEach filter map reduce

![image-20230601101221214](./Typora-image/image-20230601101221214.png)

reduce方法

作用：reduce返回函数累计处理的结果，经常用于求和等
使用场景：求和运算

![image-20230601102503005](./Typora-image/image-20230601102503005.png)

```
//    1.无起始值
        // const total = arr.reduce(function (prev, current) {
        //     return prev + current;
        // });
        // console.log(total);//60
        // 2.有起始值
        // const total = arr.reduce(function (prev, current) { return prev + current }, 6);
        // console.log(total);//66
        // 3.箭头函数
        const total = arr.reduce((prev, current) => prev + current, 6);
        console.log(total);//66
        
        
        
          const arr = [{
            name: '张三',
            salary: 10000
        }, {
            name: '李四',
            salary: 10000
        }, {
            name: '王五',
            salary: 20000
        },
        ];
        let total = 0;
        total = arr.reduce((prev, current) => prev + current.salary, 0);
        console.log(total);
        // 涨薪30%
        total = arr.reduce((prev, current) => prev + current.salary * 1.3, 0);
        console.log(total);
```

![image-20230602084550959](./Typora-image/image-20230602084550959.png)1
