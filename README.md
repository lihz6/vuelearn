## 介绍

### 声明式渲染

```html
<div id="app" v-bind:title="title">
  {{ message }}
</div>
```

```js
const app = new Vue({
  el: '#app',
  data: {
    title: `页面加载于 ${new Date().toLocaleString()}`,
    message: 'Hello Vue!',
  },
});

app.message = 'Hello World!';
```

### 条件与循环

```html
<div id="app">
  <ol v-if="todos.lenght > 0">
    <li v-for="todo in todos">
      {{ todo.text }}
    </li>
  </ol>
</div>
```

```js
const app = new Vue({
  el: '#app',
  data: {
    todos: [
      { text: '学习 JavaScript' },
      { text: '学习 Vue' },
      { text: '整个牛项目' },
    ],
  },
});
```

### 处理用户输入

```html
<div id="app">
  <p>{{ message }}</p>
  <input v-model="message" />
  <button v-on:click="count++;">点击 {{ count }} 次</button>
</div>
```

```js
const app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!',
    count: 0,
  },
});
```

### 组件化应用构建

```html
<div id="app">
  <ol>
    <!-- <li is="todo-item"/> -->
    <todo-item
      v-for="item in groceryList"
      v-bind:todo="item"
      v-bind:key="item.id"
    ></todo-item>
  </ol>
</div>
```

```js
Vue.component('todo-item', {
  props: ['todo'],
  template: '<li>{{ todo.text }}</li>',
});

const app = new Vue({
  el: '#app',
  data: {
    groceryList: [
      { id: 0, text: '蔬菜' },
      { id: 1, text: '奶酪' },
      { id: 2, text: '随便其它什么人吃的东西' },
    ],
  },
});
```
