## 在内联事件处理器中访问事件参数 

有时我们需要在内联事件处理器中访问原生 DOM 事件。你可以向该处理器方法传入一个特殊的 `$event` 变量，或者使用内联箭头函数：

```javascript
<!-- 使用特殊的 $event 变量 -->
<button @click="warn('Form cannot be submitted yet.', $event)">
 Submit
</button>

<!-- 使用内联箭头函数 -->
<button @click="(event) => warn('Form cannot be submitted yet.', event)">
 Submit
</button>function warn(message, event) {
 // 这里可以访问原生事件
 if (event) {
 event.preventDefault()
 }
 alert(message)
}
```

来自: [事件处理 | Vue.js](https://cn.vuejs.org/guide/essentials/event-handling.html#accessing-event-argument-in-inline-handlers)



我们可以用 [watchEffect 函数](https://cn.vuejs.org/api/reactivity-core.html#watcheffect) 来简化上面的代码。`watchEffect()` 允许我们自动跟踪回调的响应式依赖。上面的侦听器可以重写为：

```javascript
watchEffect(async () => {
 const response = await fetch(
 `https://jsonplaceholder.typicode.com/todos/${todoId.value}`
 )
 data.value = await response.json()
})
```

这个例子中，回调会立即执行，不需要指定 `immediate: true`。在执行期间，它会自动追踪 `todoId.value` 作为依赖（和计算属性类似）。每当 `todoId.value` 变化时，回调会再次执行。有了 `watchEffect()`，我们不再需要明确传递 `todoId` 作为源值。

来自: [侦听器 | Vue.js](https://cn.vuejs.org/guide/essentials/watchers.html)





为了方便，Vue 支持将模板中使用 kebab-case 的标签解析为使用 PascalCase 注册的组件。这意味着一个以 `MyComponent` 为名注册的组件，在模板中可以通过 `<MyComponent>` 或 `<my-component>` 引用。这让我们能够使用同样的 JavaScript 组件注册代码来配合不同来源的模板。

来自: [组件注册 | Vue.js](https://cn.vuejs.org/guide/components/registration.html)

`v-model` 可以在组件上使用以实现双向绑定。

从 Vue 3.4 开始，推荐的实现方式是使用 [`defineModel()`](https://cn.vuejs.org/api/sfc-script-setup.html#definemodel) 宏：



## 逻辑复用

#### [什么是“组合式函数”？](https://cn.vuejs.org/guide/reusability/composables.html#what-is-a-composable)

在 Vue 应用的概念中，“组合式函数”(Composables) 是一个利用 Vue 的组合式 API 来封装和复用**有状态逻辑**的函数。

当构建前端应用时，我们常常需要复用公共任务的逻辑。例如为了在不同地方格式化时间，我们可能会抽取一个可复用的日期格式化函数。这个函数封装了**无状态的逻辑**：它在接收一些输入后立刻返回所期望的输出。复用无状态逻辑的库有很多，比如你可能已经用过的 [lodash](https://lodash.com/) 或是 [date-fns](https://date-fns.org/)。

来自: [组合式函数 | Vue.js](https://cn.vuejs.org/guide/reusability/composables)



`toValue()` 是一个在 3.3 版本中新增的 API。它的设计目的是将 ref 或 getter 规范化为值。如果参数是 ref，它会返回 ref 的值；如果参数是函数，它会调用函数并返回其返回值。否则，它会原样返回参数。它的工作方式类似于 [unref()](https://cn.vuejs.org/api/reactivity-utilities.html#unref)，但对函数有特殊处理。

来自: [组合式函数 | Vue.js](https://cn.vuejs.org/guide/reusability/composables.html#async-state-example)



#### [和 Mixin 的对比](https://cn.vuejs.org/guide/reusability/composables.html#vs-mixins)

Vue 2 的用户可能会对 [mixins](https://cn.vuejs.org/api/options-composition.html#mixins) 选项比较熟悉。它也让我们能够把组件逻辑提取到可复用的单元里。然而 mixins 有三个主要的短板：

1. **不清晰的数据来源**：当使用了多个 mixin 时，实例上的数据属性来自哪个 mixin 变得不清晰，这使追溯实现和理解组件行为变得困难。这也是我们推荐在组合式函数中使用 ref + 解构模式的理由：让属性的来源在消费组件时一目了然。
2. **命名空间冲突**：多个来自不同作者的 mixin 可能会注册相同的属性名，造成命名冲突。若使用组合式函数，你可以通过在解构变量时对变量进行重命名来避免相同的键名。
3. **隐式的跨 mixin 交流**：多个 mixin 需要依赖共享的属性名来进行相互作用，这使得它们隐性地耦合在一起。而一个组合式函数的返回值可以作为另一个组合式函数的参数被传入，像普通函数那样。

基于上述理由，我们不再推荐在 Vue 3 中继续使用 mixin。保留该功能只是为了项目迁移的需求和照顾熟悉它的用户。

#### [和无渲染组件的对比](https://cn.vuejs.org/guide/reusability/composables.html#vs-renderless-components)

在组件插槽一章中，我们讨论过了基于作用域插槽的[无渲染组件](https://cn.vuejs.org/guide/components/slots.html#renderless-components)。我们甚至用它实现了一样的鼠标追踪器示例。

组合式函数相对于无渲染组件的主要优势是：组合式函数不会产生额外的组件实例开销。当在整个应用中使用时，由无渲染组件产生的额外组件实例会带来无法忽视的性能开销。

**我们推荐在纯逻辑复用时使用组合式函数，在需要同时复用逻辑和视图布局时使用无渲染组件。**

#### [和 React Hooks 的对比](https://cn.vuejs.org/guide/reusability/composables.html#vs-react-hooks)

如果你有 React 的开发经验，你可能注意到组合式函数和自定义 React hooks 非常相似。组合式 API 的一部分灵感正来自于 React hooks，Vue 的组合式函数也的确在逻辑组合能力上与 React hooks 相近。然而，Vue 的组合式函数是基于 Vue 细粒度的响应性系统，这和 React hooks 的执行模型有本质上的不同。这一话题在[组合式 API 的常见问题](https://cn.vuejs.org/guide/extras/composition-api-faq.html#comparison-with-react-hooks)中有更细致的讨论。

#### [自定义指令](https://cn.vuejs.org/guide/reusability/custom-directives.html#custom-directives)



一个自定义指令由一个包含类似组件生命周期钩子的对象来定义。钩子函数会接收到指令所绑定元素作为其参数。下面是一个自定义指令的例子，当 Vue 将元素插入到 DOM 中后，该指令会将一个 class 添加到元素中：

```vue
<script setup>
// 在模板中启用 v-highlight
const vHighlight = {
  mounted: (el) => {
    el.classList.add('is-highlight')
  }
}
</script>

<template>
  <p v-highlight>This sentence is important!</p>
</template>
```



## 内置组件



### [Transition](https://cn.vuejs.org/guide/built-ins/transition#css-based-transitions)

#### [基于 CSS 的过渡效果](https://cn.vuejs.org/guide/built-ins/transition#css-based-transitions)

#### [CSS 过渡 class](https://cn.vuejs.org/guide/built-ins/transition#transition-classes)

一共有 6 个应用于进入与离开过渡效果的 CSS class。

![过渡图示](https://cn.vuejs.org/assets/transition-classes.DYG5-69l.png)

1. `v-enter-from`：进入动画的起始状态。在元素插入之前添加，在元素插入完成后的下一帧移除。
2. `v-enter-active`：进入动画的生效状态。应用于整个进入动画阶段。在元素被插入之前添加，在过渡或动画完成之后移除。这个 class 可以被用来定义进入动画的持续时间、延迟与速度曲线类型。
3. `v-enter-to`：进入动画的结束状态。在元素插入完成后的下一帧被添加 (也就是 `v-enter-from` 被移除的同时)，在过渡或动画完成之后移除。
4. `v-leave-from`：离开动画的起始状态。在离开过渡效果被触发时立即添加，在一帧后被移除。
5. `v-leave-active`：离开动画的生效状态。应用于整个离开动画阶段。在离开过渡效果被触发时立即添加，在过渡或动画完成之后移除。这个 class 可以被用来定义离开动画的持续时间、延迟与速度曲线类型。
6. `v-leave-to`：离开动画的结束状态。在一个离开动画被触发后的下一帧被添加 (也就是 `v-leave-from` 被移除的同时)，在过渡或动画完成之后移除。

`v-enter-active` 和 `v-leave-active` 给我们提供了为进入和离开动画指定不同速度曲线的能力，我们将在下面的小节中看到一个示例。





#### [为过渡效果命名](https://cn.vuejs.org/guide/built-ins/transition#named-transitions)

我们可以给 `<Transition>` 组件传一个 `name` prop 来声明一个过渡效果名：

**对于一个有名字的过渡效果，对它起作用的过渡 class 会以其名字而不是 `v` 作为前缀。比如，上方例子中被应用的 class 将会是 `fade-enter-active` 而不是 `v-enter-active`。这个“fade”过渡的 class 应该是这样：**

```css
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
```

### [KeepAlive](https://cn.vuejs.org/guide/built-ins/keep-alive.html)

```vue
<!-- 非活跃的组件将会被缓存！ -->
<KeepAlive>
  <component :is="activeComponent" />
</KeepAlive>
```

#### [最大缓存实例数](https://cn.vuejs.org/guide/built-ins/keep-alive.html#max-cached-instances)

我们可以通过传入 `max` prop 来限制可被缓存的最大组件实例数。`<KeepAlive>` 的行为在指定了 `max` 后类似一个 [LRU 缓存](https://en.wikipedia.org/wiki/Cache_replacement_policies#Least_recently_used_(LRU))：如果缓存的实例数量即将超过指定的那个最大数量，则最久没有被访问的缓存实例将被销毁，以便为新的实例腾出空间。

```vue
<KeepAlive :max="10">
  <component :is="activeComponent" />
</KeepAlive>
```

### [Teleport](https://cn.vuejs.org/guide/built-ins/teleport.html)

将子组件的模板传送到 子组件之外的DOM结构中显示

`<Teleport>` 是一个内置组件，它可以将一个组件内部的一部分模板“传送”到该组件的 DOM 结构外层的位置去。

### [Suspense](https://cn.vuejs.org/guide/built-ins/suspense.html#loading-state)

Vue.js 的 `<Suspense>` 组件是一个用于协调异步依赖关系的内置组件，主要用于优化异步组件或异步数据加载时的用户体验。以下是该页面核心内容的解读：

---

#### **核心功能**
1. **异步组件加载状态管理**  
   当子组件包含异步操作（如 `async setup()` 或动态导入的组件）时，`<Suspense>` 允许你定义一个 **备用内容（fallback）** 在加载期间展示（如加载动画），待异步操作完成后显示正式内容。

2. **多层级异步协调**  
   `<Suspense>` 会等待所有嵌套的异步操作完成，即使它们是深层嵌套的组件，避免界面部分加载导致的闪烁问题。

---

#### **基本用法**
```vue
<template>
  <Suspense>
    <!-- 主内容：包含异步操作的组件 -->
    <AsyncComponent />

    <!-- 加载状态的回退内容 -->
    <template #fallback>
      <div>Loading...</div>
    </template>
  </Suspense>
</template>

<script setup>
// 异步组件示例
const AsyncComponent = defineAsyncComponent(() =>
  import('./AsyncComponent.vue')
)
</script>
```

---

#### **关键特性**
1. **异步 `setup()` 支持**  
   如果组件的 `setup()` 是异步的，可以直接在父级用 `<Suspense>` 包裹：
   ```vue
   <script setup>
   const data = await fetchData() // 异步操作
   </script>
   ```

2. **错误处理**  
   结合 `onErrorCaptured` 生命周期钩子捕获子组件的错误，实现错误边界：
   
   ```vue
   <script setup>
   import { onErrorCaptured } from 'vue'
   
   onErrorCaptured((error) => {
     // 处理错误（如显示错误信息）
     return false // 阻止错误继续冒泡
   })
   </script>
   ```
   
3. **事件触发**  
   `<Suspense>` 提供 `@pending`、`@resolve` 和 `@fallback` 事件，用于跟踪加载状态变化。

---

#### **注意事项**
1. **组合式 API 限制**  
   异步 `setup()` 需通过 `<Suspense>` 或 `await` 在父组件中调用，否则可能导致数据未就绪。

2. **嵌套使用**  
   多个 `<Suspense>` 可以嵌套，每个会独立处理自己的异步依赖。

3. **SSR 兼容性**  
   `<Suspense>` 在服务端渲染（SSR）中，初始请求会渲染 fallback，客户端激活后才加载内容。

---

#### **适用场景**
- 需要数据预加载的组件（如从 API 获取数据）。
- 动态导入的组件（Code Splitting）。
- 需要统一处理复杂异步依赖树的加载状态。

---

通过 `<Suspense>`，开发者可以更优雅地处理异步逻辑，提升用户对加载过程的感知体验。建议结合具体项目需求设计合理的 fallback UI 和错误处理机制。