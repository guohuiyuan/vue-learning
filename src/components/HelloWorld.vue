<template>
  <h1>{{ msg }}</h1>
  <button @click="count++">count is: {{ count }}</button>
  <p>
    Edit <code>components/HelloWorld.vue</code> to test hot module replacement.
  </p>
  <div id="bind-attribute">
    <span v-bind:title="message">
      鼠标悬停几秒钟查看此处动态绑定的提示信息！
    </span>
    <div id="event-handling">
      <p>{{ message }}</p>
      <button v-on:click="reverseMessage">反转 Message</button>
    </div>
    <div id="two-way-binding">
      <p>{{ message2 }}</p>
      <p>message2</p>
      <input v-model="message2" />
    </div>
    <div id="conditional-rendering">
      <span v-if="!!message3">现在你看到我了</span>
      <p>message3</p>
      <input v-model="message3" />
    </div>
    <div id="list-rendering">
      <ol>
        <li v-for="todo in todos" :key="todo">
          {{ todo.text }}
        </li>
      </ol>
    </div>
    <div id="todo-list-app">
      <ol>
        <!--
      现在我们为每个 todo-item 提供 todo 对象
      todo 对象是变量，即其内容可以是动态的。
      我们也需要为每个组件提供一个“key”，稍后再
      作详细解释。
    -->
        <todo-item
          v-for="item in groceryList"
          v-bind:todo="item"
          v-bind:key="item.id"
        ></todo-item>
      </ol>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      count: 0,
      message: "You loaded this page on " + new Date().toLocaleString(),
      message2: "hello world",
      message3: "",
      todos: [
        { text: "Learn JavaScript" },
        { text: "Learn Vue" },
        { text: "Build something awesome" },
      ],
       groceryList: [
        { id: 0, text: 'Vegetables' },
        { id: 1, text: 'Cheese' },
        { id: 2, text: 'Whatever else humans are supposed to eat' }
      ],
    };
  },
  methods: {
    reverseMessage() {
      this.message = this.message.split("").reverse().join("");
    },
  },
};
</script>
