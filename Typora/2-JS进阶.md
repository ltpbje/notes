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

总结

1.全局作用域有哪些？

`<script>`标签内部
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

![image-20230528103411816](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855703.png)

#### 语法

##### 语法1：基本写法

![image-20230528150034661](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855704.png)

##### 语法2：只有一个参数可以省略小括号

![image-20230528150304075](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855705.png)

##### 语法3：如果函数体只有一行代码，可以写到一行上，并且无需写return直接返回值

![image-20230528150142170](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855706.png)

##### 语法4：加括号的函数体返回对象字面量表达式

![image-20230528151931050](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855707.png)

#### 箭头函数参数

1.普通函数有arguments动态参数
2.箭头函数没有arguments动态参数，但是有剩余参数...args

箭头函数里面有arguments:动态参数吗？可以使用什么参数？

>没有arguments动态参数
>可以使用剩余参数

#### 箭头函数this

箭头函数不会创建自己的this,它只会从自己的作用域链的上一层沿用this。

![image-20230528154014105](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855708.png)

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

![image-20230528154855924](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855710.png)

# 解构赋值

目标：知道解构的语法及分类，使用解构简洁语法快速为变量赋值

**左侧**的 [ ] 用于批量声明变量    **右侧**数组的单元值将被赋值给左侧的变量

## 数组解构

![image-20230528170416124](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855711.png)

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

![image-20230529083636432](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855712.png)

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

![image-20230529094227417](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855713.png)

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

<img src="https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855714.png" alt="image-20230530100641994" />

```
 const arr = ['小米', '华为', 'vivo'];
        //forEach()不会像map()方法那样返回数组
        const a = arr.forEach((item, index) => {
            console.log(item);//数组中的元素
            console.log(index);//索引号
        });
        console.log(a);//undefined
```

![image-20230530100746717](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855715.png)

## filter ( )筛选过滤数组方法

```
 const arr = [100, 200, 300, 10, 2];
        // 筛选大于等于200的元素
        const newArr = arr.filter(item => item >= 200);
        console.log(newArr);// [200,300]
```

![image-20230530202119844](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855716.png)

1) 筛选数组

2) 返回值：返回数组，包含了符合条件的所有元素。如果没有符合条件的元素则返回空数组

3) 参数：currentValue必须写，index可选

4) ## 因为返回新数组，所以不会影响原数组



# 深入对象

## 创建对象三种方式

![image-20230531203708393](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855717.png)

![image-20230531203740422](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855718.png)

构造函数在技术上是常规函数。 不过有两个约定： 1. 它们的命名以大写字母开头。 2. 它们只能由 "new" 操作符来执行。

## 构造函数实例化执行过程

1) 利用new创建新的空对象
2) this指向新的对象
3) 执行构造函数代码,添加新的属性
4) 返回新的对象



![image-20230531210251959](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855719.png)

## 实例成员

![image-20230601091655978](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855720.png)

## 静态成员

![image-20230601091736243](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855721.png)

![image-20230601091810605](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855722.png)

## 内置构造函数

![image-20230601094142342](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855723.png)

引用类型

Object,Array,RegExp,Date

包装类型

String,Number,Boolean

### Object

![image-20230601095456370](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855724.png)

#### 三个常用静态方法（静态方法就是只有构造函数Object可以调用的）

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

![image-20230601100835127](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855725.png)

### Array

forEach filter map reduce

![image-20230601101221214](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855726.png)

reduce方法

作用：reduce返回函数累计处理的结果，经常用于求和等
使用场景：求和运算

![image-20230601102503005](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855727.png)

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



![image-20230602084550959](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855728.png)

### String

![image-20230603093652358](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306031855729.png)

### Number

![image-20230604092717444](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306051103060.png)

# 两种编程思想

## 面向过程编程

![image-20230604150700643](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306051103062.png)

## 面向对象编程

![image-20230604150717675](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306051103063.png)

![image-20230604151526609](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306051103064.png)

1.2 面向对象编程 (oop) 

 在面向对象程序开发思想中，每一个对象都是功能中心，具有明确分工。 

面向对象编程具有灵活、代码可复用、容易维护和开发的优点，更适合多人合作的大型软件项目。

  面向对象的特性： 

1) 封装性 
2) 继承性 
3) 多态性



面向过程编程 

优点：性能比面向对象高，适合跟硬件联系很紧密 的东西，例如单片机就采用的面向过程编程。

 缺点：没有面向对象易维护、易复用、易扩展 

面向对象编程 

优点：易维护、易复用、易扩展，由于面向对象有封装 、继承、多态性的特性，可以设计出低耦合的系统，使 系统 更加灵活、更加易于维护

 缺点：性能比面向过程低

==生活离不开蛋炒饭，也离不开盖浇饭，选择不同而已，只不过前端不同于其他语言，面向过程更多==

# ==构造函数==

# ==是原型对象和实例对象的爸爸==

1) 封装是面向对象思想中比较重要的一部分，js面向对象可以通过构造函数实现的封装。

2) 同样的将变量和函数组合到了一起并能通过 this 实现数据的共享，所不同的是==借助构造函数创建出来的实例对象之 间是彼此不影响的==new出来的实例对象是相互独立互不影响的

总结： 

1) 构造函数体现了面向对象的封装特性 

2) 构造函数实例创建的对象彼此独立、互不影响

构造函数的缺点

1) 封装是面向对象思想中比较重要的一部分，js面向对象可以通过构造函数实现的封装。

2) 前面我们学过的构造函数方法很好用，但是 存在==浪费内存==的问题（相同的方法它会重复生成占用空间）

![image-20230604153445778](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306051103065.png)

1.JS 实现面向对象需要借助于谁来实现？ 

​	 构造函数

2.构造函数存在什么问题？

​	 浪费内存

# ==**原型对象**==

目标：能够利用原型对象实现方法共享 

构造函数通过原型分配的函数是所有对象所 共享的。 

JavaScript 规定，每一个构造函数都有一个 prototype 属性，指向另一个对象，所以我们也称为原型对象

 这个对象可以挂载函数，对象实例化不会多次创建原型上函数，节约内存 

==我们可以把那些不变的方法，直接定义在 prototype 对象上，这样所有对象的实例就可以共享这些方法。==

==构造函数和原型对象中的this 都指向 实例化的对象==

![image-20230604162831134](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306051103066.png)

1) 原型是什么 ？

> 一个对象，我们也称为 prototype 为原型对象 

2) 原型的作用是什么 ？ 

> 共享方法 
>
> 可以把那些不变的方法，直接定义在 prototype 对象上

3. 构造函数和原型里面的this指向谁 ？ 

> 实例化的对象

## constructor

##  属性指向自己的爸爸

在哪里？每个原型对象里面都有个`constructor` 属性（constructor 构造函数） 

==作用：该属性指向该原型对象的构造函数， 简单理解，就是指向我的爸爸，我是有爸爸的孩子==

![image-20230604204734036](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306051103067.png)

==使用场景==： 如果有多个对象的方法，我们可以给原型对象采取对象形式赋值. 但是这样就会覆盖构造函数原型对象原来的内容，这样修改后的原型对象 constructor 就不再指向当前构造函数了 此时，我们可以在修改后的原型对象中，添加一个 constructor 指向原来的构造函数。

```js
  function Star(uname, age) {
            that = this;
            this.uname = uname;
            this.age = age;
        }
        Star.prototype = {
            // 手动使原型对象指向构造函数
            constructor: Star,
            sing: () => {
                console.log('唱歌');
            },
            dance: () => {
                console.log('跳舞');
            }
        }
        const ldh = new Star('刘德华', '55');
        const zxy = new Star('张学友', '58');
        console.log(Star.prototype.constructor);//f Object()
        console.log(Star.prototype.constructor);//f Star()
```

构造函数可以创建实例对象，构造函数还有一个原型对象，一些公共的属性或者方法放到这个原型对象身上 但是 为啥实例对象可以访问原型对象里面的属性和方法呢？

`对象都会有一个属性__proto__ `指向`构造函数的 prototype 原型对象`，之所以我们对象可以使用构造函数 prototype 原型对象的属性和方法，就是因为对象有 `__proto__ 原型`的存在。

![image-20230604211642131](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306051103068.png)

1. prototype是什么？哪里来的？

   > 原型（原型对象）
   >
   > 构造函数都自动有原型 

  2. constructor属性在哪里？作用干啥的？ 

> prototype原型和对象原型`__proto__`里面都有 
>
>  都指向创建实例对象/原型的构造函数 

3. `__proto__`属性在哪里？指向谁？  

   > 在实例对象里面  指向原型 prototype

![image-20230605083925827](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306051103069.png)

```js
<script>
function Person(name) {
	this.name = name;
};
const peppa = new Person('佩奇');
Person.prototype.sayHi = function () {
	console.log('Hi');
}
console.log(Person);
console.log(peppa);
console.log(peppa.constructor);//           实例对象.constructor  指向=>  构造函数
console.log(Person.prototype.constructor);//原型对象.constructor  指向=>  构造函数
// 对象原型是随着实例对象产生而自动创造的
console.log(peppa.__proto__);//             对象原型              指向=>  原型对象
</script>
```

## ==原型继承==

原型继承 

继承是面向对象编程的另一个特征，通过继承进一步提升代码封装的程度，JavaScript 中大多是借助原型对象实现继承 的特性。 龙生龙、凤生凤、老鼠的儿子会打洞描述的正是继承的含义。

1. 封装-抽取公共部分 把男人和女人公共的部分抽取出来放到人类里面

   ```js
   function People() {
        this.eyes = 2;
        this.head = 1;
        this.sayHi = function () {
            console.log('Hi');
        }``
    };
   ```

   

2. 继承-让男人和女人都能继承人类的一些属性和方法  把男人女人公共的属性和方法抽取出来 People  然后赋值给Man的原型对象，可以共享这些属性和方法  注意让constructor指回Man这个构造函数

3. 问题： 如果我们给男人添加了一个吸烟的方法，发现女人自动也添加这个方法

​     --原因 男人和女人都同时使用了同一个对象，根据引用类型的特点，他们指向同一个对象，修改一个就会都影响

![image-20230606200214235](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306101719273.png)

4. 解决： 需求：男人和女人不要使用同一个对象，但是不同对象里面包含相同的属性和方法 答案：

构造函数 new 每次都会创建一个新的对象

5. 继承写法完善

```js
 function Person() {
            this.eyes = 2;
            this.head = 1;
            this.sayHi = function () {
                console.log('Hi');
            }
        };
        function Woman() {
            this.baby = function () {
                console.log('宝贝');
            };
        };
        function Man() {

        };
        console.log(new Person());
        // 利用原型对象添加公共的属性和方法
        Woman.prototype = new Person();
        // 手动将原型对象指向构造函数
        Woman.prototype.constructor = Woman;
        const red = new Woman();
        console.log(red);
        console.log(red.eyes);

        Man.prototype = new Person();
        Man.prototype.constructor = Man;
        const pink = new Man();
        console.log(pink);
        console.log(pink.eyes);
        console.log(pink.sayHi());
```

### ==思路==

真正做这个案例，我们的思路应该是先考虑大的，后考虑小的

1. 人类共有的属性和方法有那些，然后做个构造函数，进行封装，一般公共属性写到构造函数内部，公共方法，挂载 到构造函数原型身上。
2.  男人继承人类的属性和方法，之后创建自己独有的属性和方法 
3. 女人同理

## ==原型链==

只要是`原型对象`就有`constructor`

只要是`对象`就有`__proto__`对象原型

基于原型对象的继承使得不同构造函数的原型对象关联在一起，并且这种关联的关系是一种链状的结构，我们将原型对 象的链状结构关系称为原型链

 ==原型链其实就是一个查找规则== 

① 当访问一个对象的属性（包括方法）时，首先查找这个对象自身有没有该属性。

② 如果没有就查找它的原型（也就是`__proto__`指向的 prototype 原型对象） 

③ 如果还没有就查找原型对象的原型（Object的原型对象）

④ 依此类推一直找到 Object 为止（null） 

⑤` __proto__`对象原型的意义就在于为对象成员查找机制提供一个方向，或者说一条路线 

⑥ 可以使用` instanceof `运算符用于检测构造函数的 `prototype `属性是否出现在某个实例对象的原型链上

![image-20230606204253514](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306101719275.png)

## 综合案例

消息提示对象封装 分析需求：

1. 定义模态框 Modal 构造函数，用来创建对象 

2. 模态框具备 打开功能 open 方法 （按钮点击可以打开模态框） 

3. 模态框 具备关闭功能 close 方法 

   问： open 和 close 方法 写到哪里？ 构造函数的原型对象上，共享方法 所以可以分为三个模块，`构造函数, open方法, close方法`

消息提示对象封装 

步骤：

①：Modal 构造函数 制作 - 需要的公共属性： 标题（title）、提示信息内容（message） 可以设置默认参数 - 在页面中创建模态框 (1)创建div标签可以命名为：`modalBox` 

(2)div标签的类名为 `modal` 

(3)标签内部添加 基本结构，并填入相关数据

①：open方法 - 写到构造函数的原型对象身上 - 把刚才创建的`modalBox` 添加到 页面 body 标签中 - open 打开的本质就是 把创建标签添加到页面中 - 点击按钮， 实例化对象，传入对应的参数，并执行 open 方法

①：close方法 - 写到构造函数的原型对象身上 - 把刚才创建的`modalBox` 从页面 body 标签中 删除 - 需要注意，x 删除按钮绑定事件，要写到open里面添加 因为open是往页面中添加元素，同时顺便绑定事件

原型对象上面挂在函数，可以实现共享，反而更加节省内存，因为不需要每次都创建这个函数

# `JS`高级第四天

## 1.深浅拷贝

深浅拷贝 开发中我们经常需要复制一个对象。如果直接用赋值会有下面问题：

![image-20230608171759410](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306101719276.png)

这好比有同学来pink老师这里拷视频，竟然用的是剪切…气人不

### 1.1 浅拷贝 

首先浅拷贝和深拷贝只针对引用类型 

浅拷贝：拷贝的是地址 常见方法： 

1. 拷贝对象：`Object.assgin()` / 展开运算符 {...obj} 拷贝对象 
2. 拷贝数组：`Array.prototype.concat()` 或者 [...arr]

```js
 const obj = {
     name: 'pink老师',
     age: 20,
 };
// const o = { ...obj };
const o = {};
Object.assign(o, obj);
o.age = 18;
console.log(o);
console.log(obj);
```

小问题

![image-20230608175819392](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306101719277.png)

如果是简单数据类型拷贝值，引用数据类型拷贝的是地址 (简单理解： 如果是单层对象，没问题，如果有多层就有问题)


1. 直接赋值和浅拷贝有什么区别？ 
   直接赋值的方法，只要是对象，都会相互影响，因为是直接拷贝对象栈里面的地址 
   浅拷贝如果是一层对象，不相互影响，如果出现多层对象拷贝还会 相互影响 
1. 浅拷贝怎么理解？
      拷贝对象之后，里面的属性值是简单数据类型直接拷贝值  如果属性值是引用数据类型则拷贝的是地址

### 1.2 深拷贝 

### 实现深拷贝有三种方法 

首先浅拷贝和深拷贝只针对引用类型 深拷贝：拷贝的是对象，不是地址 常见方法： 

1. 通过递归实现深拷贝 

   ```js
    const obj = {
        name: 'pink',
        age: 18,
        hobby: ['乒乓球', '足球', '排球'],
        family: {
            baby: '小pink'
        }
    }
   const o = {};
   function deppCopy(newObj, oldObj) {
       for (let k in oldObj) {
           // 必须先数组然后再对象
           // 因为数组也属于对象
           if (oldObj[k] instanceof Array) {
               newObj[k] = [];
               deppCopy(newObj[k], oldObj[k]);
           } else if (oldObj[k] instanceof Object) {
               newObj[k] = {};
               deppCopy(newObj[k], oldObj[k]);
           }
           else {
               newObj[k] = oldObj[k];
           }
       }
   };
   deppCopy(o, obj);
   o.age = 20;
   o.hobby[1] = '篮球';
   o.family.baby = '老pink';
   console.log(obj);
   console.log(o);
   ```

   

2. `lodash/cloneDeep`

   ```js
   const obj = {
       name: 'pink',
       age: 18,
       hobby: ['乒乓球', '足球', '排球'],
       family: {
           baby: '小pink'
       }
   };
   const o = _.cloneDeep(obj);
   o.age = 20;
   console.log(o);
   console.log(obj);
   ```

   


3. 通过`JSON.stringify()`实现

   ```js
    const obj = {
        name: 'pink',
        age: 18,
        hobby: ['乒乓球', '足球', '排球'],
        family: {
            baby: '小pink'
        }
    };
   const o = JSON.parse(JSON.stringify(obj));
   console.log(o);
   ```

   

## 异常处理

### throw抛异常

异常处理是指预估代码执行过程中可能发生的错误，然后最大程度的避免错误的发生导致整个程序无法继续运行

```js
 function fn(x, y) {
  	if (!x || !y) {
         throw new Error('没有参数传过来');
     }
     else return x + y;
 };
fn();
```

总结： 

1) throw 抛出异常信息，程序也会终止执行
2) throw 后面跟的是错误提示信息 
3) Error 对象配合 throw 使用，能够设置更详细的错误信息

### try/catch 捕获错误信息

我们可以通过try / catch 捕获错误信息（浏览器提供的错误信息） try 试试 catch 拦住 finally 最后

总结： 

1. try...catch 用于捕获错误信息 
2. 将预估可能发生错误的代码写在 try 代码段中 
3. 如果 try 代码段中出现错误后，会执行 catch 代码段，并截获到错误信息
4. finally 不管是否有错误，都会执行

总结

1) 捕获异常我们用那3个关键字？可能会出现的错误代码写到谁里面
       try catch finally                                                                 try

2) 怎么调用错误信息？ 
       利用catch的参数

   ```html
    <p>111</p>
       <script>
           function foo() {
               try {                  //试一试
                   const p = document.querySelector('p');
                   p.style.color = 'red';
               } catch (err) {        //拦截错误
                   console.log(err.message);
                   throw new Error('你看看，选择器错误了');
               } finally {
                   alert('无论错误与否我都会执行');
               }
               console.log('当没有错误时我才会执行');
           };
           foo();
       </script>
   ```

### debugger

### 相当于断点调试 


   我们可以通过try / catch 捕获错误信息（浏览器提供的错误信息）

   

![image-20230609142928797](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306101719278.png)

## 处理this

是 JavaScript 最具“魅惑”的知识点，不同的应用场合 this 的取值可能会有意想不到的结果，在此我们对以往学习 过的关于【 this 默认的取值】情况进行归纳和总结。 目标： 了解函数中 this 在不同场景下的默认值，知道动态指定函数 this 值的方法 学习路径： 

1. 普通函数this指向 
2.  箭头函数this指向

### this指向-普通函数 

目标： 能说出普通函数的this指向 普通函数的调用方式决定了 this 的值，即==【谁调用 this 的值指向谁】==

普通函数this指向我们怎么记忆？

   【谁调用 this 的值指向谁】 
普通函数严格模式下指向谁？
    严格模式下指向 undefined

### this指向-箭头函数 

箭头函数中的 this 与普通函数完全不同，也不受调用方式的影响，事实上箭头函数中并不存在 this ！ 

1. 箭头函数会默认帮我们绑定外层 this 的值，所以在箭头函数中 this 的值和外层的 this 是一样的 
2. 箭头函数中的this引用的就是最近作用域中的this 
3. 向外层作用域中，一层一层查找this，直到有this的定义

总结： 

1. 函数内不存在this，沿用上一级的 
2. 不适用  构造函数，原型函数，`Dom`事件函数等等 
3. 适用  需要使用上层this的地方 
4.  使用正确的话，它会在很多地方带来方便，后面我们会大量使用慢慢体会

### 改变this的指向

####  `1.`call() –了解

 使用 call 方法==调用函数==，同时指定被调用函数中 this 的值  语法： `fun.call(thisArg, arg1, arg2, ...)` 

` thisArg`：在 fun 函数运行时指定的 this 值  `arg1，arg2`：传递的其他参数  返回值就是函数的返回值，因为它就是调用函数

```js
 const obj = {
            name: 'pink',
            age: 18
        }
        function fn(x, y) {
            console.log(this);
            console.log(x + y);
        }
        fn.call(obj, 1, 2);
```

call的作用是？ 

 调用函数，并可以改变被调用函数里面的this指向 

call 里面第一个参数是 指定this， 其余是实参，传递的参数 整体做个了解，后期用的很少

#### `2.`apply()-理解 

使用 apply 方法调用函数，同时指定被调用函数中 this 的值 

 语法：  `thisArg`：在fun函数运行时指定的 this 值 

` argsArray`：传递的值，必须包含在数组里面  返回值就是函数的返回值，因为它就是调用函数  因此 apply 主要跟数组有关系，比如使用 `Math.max()` 求数组的最大值

call和apply的区别是？ 

 都是调用函数，都能改变this指向 

 参数不一样，apply传递的必须是数组

```js
 const obj = {
     age: 18
 };
function fn(x, y) {
    console.log(this);
    console.log(x + y);
};
fn.apply(obj, [1, 2]);
const arr = [12, 44, 33, 22];
const max = Math.max.apply(null, arr);
const min = Math.min.apply(null, arr);
console.log(max);
console.log(min);
```

#### `3.`==bind()-重点==

 bind() 方法==不会调用函数==。但是能改变函数内部this 指向 

 语法：    `fun.bind(thisArg, arg1, arg2, ...)`

`thisArg`：在 fun 函数运行时指定的 this 值 

`arg1，arg2`：传递的其他参数  返回由指定的 this 值和初始化参数改造的 原函数拷贝 （新函数）   因此当我们只是想改变 this 指向，并且不想调用这个函数的时候，可以使用 bind，比如改变定时器内部的 this指向.

```js
const obj = {
    age: 18
};
function fn(x, y) {
    console.log(this);
    console.log(x + y);
};
const foo = fn.bind(obj, 2, 3);
console.log(foo);
foo();
```



#### ==call apply bind 总结==

 相同点: 

> 都可以改变函数内部的this指向.

 区别点: 

> call 和 apply 会调用函数, 并且改变函数内部this指向. 

call 和 apply 传递的参数不一样, call 传递参数 `aru1, aru2..`形式 apply 必须`数组形式[arg]`

bind 不会调用函数, 可以改变函数内部this指向.

主要应用场景: 

call 调用函数并且可以传递参数 

apply 经常跟数组有关系. 比如借助于数学对象实现数组最大值最小值

 bind 不调用函数,但是还想改变this指向. 比如改变定时器内部的this指向.

## 性能优化

### 防抖`(debounce)`

> 防抖：单位时间内，频繁触发事件，只执行最后一次

举个栗子：王者荣耀回城，只要被打断就需要重新来

使用场景：
    搜索框搜索输入。只需用户最后一次输入完，再发送请求 手机号、邮箱验证输入检测

![image-20230611103658124](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306111953259.png)

```js
<div class="box"></div>
    <script src="./lodash.min.js"></script>
    <script>
        const box = document.querySelector('.box');
        let i = 0;
        function mouseMove() {
            box.innerHTML = ++i;
        }
        //1. lodash实现防抖
        // box.addEventListener('mousemove', _.debounce(mouseMove,1000));
        // 2.防抖函数
        function debounce(fn, t) {
            let timer;
            return function () {
                if (timer) clearTimeout(timer);
                timer = setTimeout(fn, t);
            };
        };
        //                                因 此处的debounce()带小括号会直接调用执行 所以要用到return
        box.addEventListener('mousemove', debounce(mouseMove, 200));
    </script>
```

### 节流 

节流（throttle） 

所谓节流，就是指连续触发事件但是在 n 秒中只执行一次函数 

只有等到了上一个人做完核酸，整个动作完成了， 第二个人才能排队跟上

4.2节流-throttle
节流

> 节流：单位时间内，频繁触发事件，只执行一次

举个栗子：

> 触发王者荣耀技能冷却，期间无法继续释放技能

和平精英`98k`换子弹期间不能射击
使用场景：

高频事件：鼠标移动`mousemove`、页面尺寸缩放resize、滚动条滚动scroll等等

![image-20230611154624702](https://ltpbje.oss-cn-zhangjiakou.aliyuncs.com/img/202306111953261.png)

``````````````js
<div class="box"></div>
    <script src="./lodash.min.js"></script>
    <script>
        const box = document.querySelector('.box');
        let i = 0;
        function mouseMove() {
            box.innerHTML = ++i;
        }
        // 1.lodash来实现节流
        // box.addEventListener('mousemove', _.throttle(mouseMove,3000));
        // 2.利用函数实现节流
        function throttle(fn, t) {
            let timer = null;
            return function () {
                if (!timer) {
                    timer = setTimeout(function () {
                        fn();
                        timer = null
                    }, t);
                };
            };
        };
        box.addEventListener('mousemove', throttle(mouseMove, 1000));
    </script>
``````````````

### 总结

| 性能优化 |                   说明                    |                           使用场景                           |
| :------: | :---------------------------------------: | :----------------------------------------------------------: |
|   防抖   | 单位时间内频繁触发事件,==只执行最后一次== |           搜索框搜索输入、手机号、邮箱验证输入检测           |
|   节流   |   单位时间内频繁触发事件,==只执行一次==   | 高频事件：鼠标移动`mousemove`、页面尺寸缩放resize、滚动条滚动scroll等等 |



## 节流综合案例

页面打开，可以记录上一次的视频播放位置 分析： 

两个事件: 

①：`ontimeupdate` 事件在视频/音频（audio/video）当前的播放位置发送改变时触发 

②：`onloadeddata` 事件在当前帧的数据加载完成且还没有足够的数据播放视频/音频（audio/video）的 下一帧时触发 谁需要节流？ 

`ontimeupdate` ， 触发频次太高了，我们可以设定 1秒钟触发一次

思路： 

1.在`ontimeupdate`事件触发的时候，每隔1秒钟，就记录当前时间到本地存储 

2.下次打开页面， `onloadeddata` 事件触发，就可以从本地存储取出时间，让视频从取出的时间播放，如 果没有就默认为0s 3. 获得当前时间 `video.currentTime`



delete是干什么的： 

#  牛客网评论区

- ​    ==delete 操作符用于删除对象的某个属性；==如果没有指向这个属性的引用，那它最终会被释放。

`typeof` 能判断类型有：number、string、boolean、symbol、undefined、function；  **object、****array、null** 的变量都返回 object 

<img src='https://uploadfiles.nowcoder.com/images/20190829/990177409_1567082310187_97C622A575935FE641B060B0ED909865'>

`Object.prototype.toString() `为 Object 对象的实例方法，默认情况下（即不重写该方法），返回参数的类型字符串。

<img src='https://uploadfiles.nowcoder.com/images/20190829/990177409_1567082993145_78F6838F9534BC5011776164925615B5'>

Array 为` js `的原生对象，它有一个静态方法：`Array.isArray()`，能判断参数1是否为数组 

 

   <img src='https://uploadfiles.nowcoder.com/images/20190829/990177409_1567082310187_97C622A575935FE641B060B0ED909865'>

### class和let一样都有暂时性死区，在被声明前无法访问

也就是在当前作用域能找到，但是要在声明后才能访问
**`es6中的class`和`let const`一样都不存在提升
（实际存在提升，只是因为`TDZ`的作用，并不会像var那样得到undefined,而是直接抛出错误）**

临时死区（Temporal Dead Zone），简写为` TDZ`。

`let` 和 `const` 声明的变量不会被提升到[作用域](https://so.csdn.net/so/search?q=作用域&spm=1001.2101.3001.7020)顶部，如果在声明前访问这些变量，会导致错误：

```js
原来的代码
var a = 1;
function test(){
    //console.log(a) 位置A
class a {}
   // console.log(a) 位置B
}
test();

实际上提升后的
var a = 1;
function test(){
    console.log(a) 位置A //在test()作用域内找得到a
//是一个class但是存在TDZ暂时性死区，访问报错
    class a {}
    console.log(a) 位置B //a已经声明创建出来了
}
test()
```

-   in操作符，对于数组属性需要指定数字形式的**索引值**来表示数组的属性名称（固有属性除外，如length）。  
-    所以说在这里，1 in [1]并不是表示数字1在不在数组里。而是表示数组中含不含有1这个索引index值。 数组长度为1，所以只含有的index值为0，这个表达式返回`fasle`。  

- 任何数值除以0都会导致错误而终止程序执行。但是在 JavaScript 中，**会返回出特殊的值**，因此不会影响程序的执行。  
-    比0大的数除以0，则会得到无穷大，所以 js 用 Infinity 来显示出来。  
-    也就是1/0得到的是Infinity。`isNaN(1/0)`返回的是`false`。但是`isNaN(0/0)`返回的就是true  

1 && 2 > 1，先判断右边的表达式，2>1返回true。1 && true返回的结果也是true。\>号的权重大于&&，所以先是右边开始

**Array对象方法**

<img src= 'https://uploadfiles.nowcoder.com/images/20170801/9067279_1501580014742_4B001C5F03B58BB2DED6B768AE0D6761'>

` js`基本数据类型包括： 

 

  1.Number 

  `typeof`  123 =>"number"  

   2.String  

   typeof  `'abc'` =>"string"  

   3.Boolean  

   `typeof   true `=>"boolean"  

​    4.Function   

   ` typeof   console.log() `=>"function"   

​    5.Object   

   `typeof   `null    =>"object"  

 `  typeof  ` { } =>"object"  

  ` typeof  ` [ ] =>"object"  

   6.Undefined  

   `typeof`   undefined =>"undefined"  

   题中的Array属于数组对象  

   `typeof` new Array()  =>"object"  

   值得一提的是`typeof`打印出的类型都是字符串类型，且首字母小写  

   例如：typeof(typeof undefined) =>"string"  
