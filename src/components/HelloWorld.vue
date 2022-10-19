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
        <!-- <todoitem
          v-for="item in groceryList"
          :text="item.text"
          :key="item.id"
        ></todoitem> -->
      </ol>
    </div>
    <div id="todo-list-example">
      <form v-on:submit.prevent="addNewTodo">
        <label for="new-todo">Add a todo</label>
        <input
          v-model="newTodoText"
          id="new-todo"
          placeholder="E.g. Feed the cat"
        />
        <button>Add</button>
      </form>
      <ul>
        <todoitem
          v-for="(todo, index) in todos"
          :key="todo.id"
          :title="todo.title"
          @remove="todos.splice(index, 1)"
        ></todoitem>
      </ul>
    </div>
  </div>
</template>

<script>
import todoitem from "./Item.vue";
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  components: {
    todoitem,
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
        { id: 0, text: "Vegetables" },
        { id: 1, text: "Cheese" },
        { id: 2, text: "Whatever else humans are supposed to eat" },
      ],
      newTodoText: "",
      todos: [
        {
          id: 1,
          title: "Do the dishes",
        },
        {
          id: 2,
          title: "Take out the trash",
        },
        {
          id: 3,
          title: "Mow the lawn",
        },
      ],
      nextTodoId: 4,
    };
  },
  methods: {
    reverseMessage() {
      this.message = this.message.split("").reverse().join("");
    },
    addNewTodo() {
      this.todos.push({
        id: this.nextTodoId++,
        title: this.newTodoText,
      });
      this.newTodoText = "";
    },
  },
};
</script>
