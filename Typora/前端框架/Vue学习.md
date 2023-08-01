[Vue阶段作业地址 ](https://gitee.com/jepsonpp/vue-homework/blob/master/Vue%E5%9F%BA%E7%A1%80.md)

# Vue 核心技术与实战 day01

Vue 快速上手 

Vue 概念 / 创建实例 / 插值表达式 / 响应式特性 / 开发者工具  

Vue 指令 

v-html / v-show / v-if / v-else / v-on / v-bind / v-for / v-model

综合案例 - 小黑记事本 

列表渲染 / 删除功能 / 添加功能 / 底部统计 / 清空

![image-20230801152120432](./../Typora/Typora-image/image-20230801152120432.png)

## Vue快速上手

### Vue 是什么 

 概念：Vue 是一个用于 **构建用户界面** 的 渐进式 框架

​                            基于数据渲染出用户看到的页面

![image-20230801153622808](./../Typora/Typora-image/image-20230801153622808.png)

Vue 的两种使用方式： 

① Vue 核心包开发 

场景：局部 模块改造 

② Vue 核心包 & Vue 插件 工程化开发 

场景：整站 开发

![image-20230801153739417](./../Typora/Typora-image/image-20230801153739417.png)

![image-20230801153814975](./../Typora/Typora-image/image-20230801153814975.png)

Vue是什么？

 Vue 是一个用于 构建用户界面 的 渐进式 框架 

1. 构建用户界面：基于 数据 动态 渲染 页面 

2. 渐进式：循序渐进的学习 

3. 框架：一套完整的项目解决方案，`提升开发效率↑ (理解记忆规则)` 

​                                                                              规则→ 官网

### 创建 Vue 实例，初始化

![image-20230801154255730](./../Typora/Typora-image/image-20230801154255730.png)

创建 Vue 实例，初始化渲染的核心步骤：

1. 准备容器 

2. 引包 (官网) - 开发版本 / 生产版本 

3. 创建 Vue 实例 new Vue() 

4. 指定配置项 el data => 渲染数据 

① el 指定挂载点，选择器指定控制的是哪个盒子 

② data 提供数据