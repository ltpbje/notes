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