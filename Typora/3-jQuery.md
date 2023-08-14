# 核心函数

## 1.将它作为工具类使用

 \- 在核心函数中jQuery为我们提供了多个工具方法

## 2.将它作为函数使用

### 将一个函数作为$的参数

​	 		- 这个函数会在文档加载完毕之后执行

​             - 相当于： document.addEventListener("DOMContentLoaded", function(){})

### 将选择器字符串作为参数

\- jQuery自动去网页中查找元素

​                \- 作用类似于 document.querySelectorAll("...")

​                \- 注意：

​                  通过jQuery核心函数查询到的结果并不是原生的DOM对象，

​                    而是一个经过jQuery包装过的新的对象，这个对象我们称其为jQuery对象

​                    jQuery对象中为我们提供了很多新的方法，方便我们做各种DOM操作

​                      但是jQuery对象不能直接调用原生DOM对象的方法

​                      通过我们为jQuery对象命名时，会使用$开头，加以区分

###  将DOM对象作为参数

可以将DOM对象转换为jQuery对象，从而使用jQuery对象的方法

### 将html代码作为参数

会根据html代码来创建元素（仍是jQuery对象）

# jQuery对象

## 通过jQuery核心函数获取到的对象就是jQuery对象

##  jQuery对象是jQuery中定义的对象

​          可以将其理解为是DOM对象的升级版，在jQuery对象中为我们提供了很多简单易用的方法

​            来帮助我们简化DOM操作

## jQuery对象本质上是一个DOM对象的数组（伪数组）

​          可以通过索引获取jQuery对象中的DOM对象

## 当我们修改jQuery对象时，它会自动修改jQuery中的所有元素

​	这一特点称为jQuery的==隐式迭代==

## 通常情况下，jQuery对象方法的返回值依然是一个jQuery对象

​          所以我们可以在调用一个方法后继续调用其他的jQuery对象的方法

​          这一特性，称为jQuery对象的 链式调用

# jQuery对象的方法

## 常用方法

### 类名相关的方法

addClass()

- 为jQuery对象添加一个或多个class

hasClass()

- 检查jQuery对象是否含有某个class

removeClass()

- 删除jQuery对象的指定class

toggleClass()

- 切换jQuery对象的指定class

clone()

- 复制jQuery元素

### 操作父元素的方法

unwrap()

- 去除父元素

wrap()

- 添加父元素

wrapAll()

- 添加父元素

wrapInner()

- 在元素内部增加一层

------

### 添加子元素方法

append()

- 添加子元素

appendTo()

- 添加到父元素

prepend()

- 向前添加子元素

prependTo()

- 添加到父元素前

html()

- 读取或设置html代码

text()

- 读取或设置文本内容

  ---------



after()

- 向后边添加元素

insertAfter()

- 将元素添加到某元素的后边

before()

- 向前边添加元素

insertBefore()

- 将元素添加到某元素的前边

detach()

- 删除元素（保留元素上的事件）

empty()

- 删除所有子元素

remove()

- 删除元素

------

replaceAll()

- 替换某个元素

replaceWith()

- 被某个元素替换

------

attr()

- 设置/获取元素的指定属性
- 布尔值属性会返回实际值

prop()

- 设置/获取元素的指定属性
- 布尔值属性会返回布尔值

removeAttr()

- 移除属性

removeProp()

- 移除属性

val()

- 设置/获取元素的value属性

------

css()

- 读取/设置元素的css样式

height()

- 读取/设置元素的高度

width()

- 读取/设置元素的宽度

innerHeight()

- 读取/设置元素的内部高度

innerWidth()

- 读取/设置元素的内部宽度

outerHeight()

- 读取/设置元素可见框的高度

outerWidth()

- 读取/设置元素可见框的宽度

offset()

- 读取/设置元素的偏移量

position()

- 读取元素相当于包含块的偏移量

scrollLeft()

- 读取/设置元素水平滚动条的位置

scrollTop()

- 读取/设置元素垂直滚动条的位置

------

eq()

- 获取指定索引的元素

even()

- 获取索引为偶数的元素

odd()

- 获取索引为奇数的元素

filter()

- 筛选元素

first()

- 获取第一个元素

last()

- 获取最后一个元素

has()

- 获取含有指定后代的元素

is()

- 检查是否含有某元素

map()

- 获取对象中的指定数据

slice()

- 截取元素（切片）

------

add()

- 创建包含当前元素的新的jQuery对象

addBack()

- 将之前操作的集合中的元素添加到当前集合中

contents()

- 获取当前jQuery对象的所有子节点（包括文本节点）

end()

- 将筛选过的列表恢复到之前的状态

not()

- 从列表中去除符合条件的元素

------

children()

- 获取子元素

closest()

- 获取离当前元素最近的指定元素

find()

- 查询指定的后代元素

next()

- 获取后一个兄弟元素

nextAll()

- 获取后边所有的兄弟元素

nextUntil()

- 获取后边指定位置的兄弟元素

offsetParent()

- 获取定位父元素

parent()

- 获取父元素

parents()

- 获取所有的祖先元素

parensUntil()

- 获取指定的祖先元素

prev()

- 获取前边的兄弟元素

prevAll()

- 获取前边所有的兄弟元素

prevUntil()

- 获取指定的兄弟元素

siblings()

- 获取所有的兄弟元素