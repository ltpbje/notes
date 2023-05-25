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
