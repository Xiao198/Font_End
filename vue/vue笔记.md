## vue查漏补缺
1. Object.freeze()会使某个数据无法被响应。

```js
var obj = {
  foo: 'bar'
}

Object.freeze(obj)

new Vue({
  el: '#app',
  data: obj
})
```

2. vue中，不要在方法或生命周期函数中使用箭头函数。因为箭头函数没有this，无法定位到vue实例对象。

3. vue除了使用模板语法，也可以直接写render函数使用jsx语法。

4. v-html很容易引起xss攻击。

5. 计算属性 vs 方法

   - 计算属性是基于它们的响应式依赖进行缓存的。只有响应式依赖发生改变时它们才会重新求值。以下计算属性不再更新：

   ```js
   computed: {
     now: function () {
       return Date.now()
     }
   }
   ```

   - 每当重新触发渲染的时候，调用方法总会再次执行函数。（没有缓存）

6. 计算属性 vs 监听属性

   - 计算属性支持缓存，只有当依赖数据发生改变时，才会重新计算。监听属性不支持缓存，数据变化，直接会触发相应的操作。
   - 计算属性不支持异步，当computed内有异步操作时无效，无法监听数据的变化。

7. v-if与v-show

   - v-if会确保在切换过程中条件块内的事件监听器以及子组件适当的被销毁和重建。v-if也是惰性的，如果在初始渲染时条件为假，则不进行渲染，只有第一次会真时才开始渲染条件块。
   - v-show不管初始条件时什么，元素都会被渲染，并且只是简单的基于css进行切换。
   - 一般来说，v-if具有更高的切换开销，v-show有更高的初始渲染开销。因此，如果需要非常频繁的切换，使用v-show；如果在运行时条件改变很少，则使用v-if较好。

8. 不推荐v-if和v-for一起使用。

   - v-for具有比v-if更高的优先级。这意味着v-if将分别重复运行于每个v-for循环中，如果你是想为部分项渲染节点时，可以使用。

     ```js
     <li v-for="todo in todos" v-if="!todo.isComplete">
       {{ todo }}
     </li>
     ```

   - 如果你的目的是有条件的跳过循环的执行，那么将v-if置于外层元素或<template>上。

     ```js
     <ul v-if="todos.length">
       <li v-for="todo in todos">
         {{ todo }}
       </li>
     </ul>
     <p v-else>No todos left!</p>
     ```

9. vue2 如果监测数组变化/对象变化

   - 对象的监听是直接递归使用**Object.defineProperty**重新定义数组的每个属性，而数据是**改写数组的7个数组方法**：push，pop，shift，unshift，sort，splice，reverse

10. vue data为什么必须是函数不能是对象？

    - vue组件是可复用的vue实例，一个组件被创建好之后，就可能被用在各个地方，而组件不管被复用了多少次，组件中的data数据都应该是相互隔离，互不影响的。因此组件内的data必须是一个函数，每次返回一个新的数据对象。

11. vue组件注册有两种

    - 全局注册

      ```js
      Vue.component('my-component-name', {
        // ... options ...
      })
      ```

    - 局部注册

      ```js
      const export new Vue({
      	data:,
      	components:...
      })
      ```

12. vue单向数据流

    - 父子组件依托prop形成了一个单向下行绑定：父级prop的更新会向下流动到子组件中，反过来则不行。这样会防止从子组件意外变更父级组件的状态，从而导致你的应用的数据流向难以理解。