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
    <div>
      <span>Multiline message is:</span>
      <p style="white-space: pre-line">{{ message }}</p>
      <br />
      <textarea v-model="message" placeholder="add multiple lines"></textarea>
    </div>
    <div>
      <input type="checkbox" id="checkbox" v-model="checked" />
      <label for="checkbox">{{ checked }}</label>
    </div>
    <div id="v-model-multiple-checkboxes">
      <input type="checkbox" id="jack" value="Jack" v-model="checkedNames" />
      <label for="jack">Jack</label>
      <input type="checkbox" id="john" value="John" v-model="checkedNames" />
      <label for="john">John</label>
      <input type="checkbox" id="mike" value="Mike" v-model="checkedNames" />
      <label for="mike">Mike</label>
      <br />
      <span>Checked names: {{ checkedNames }}</span>
    </div>
    <div id="v-model-radiobutton">
      <input type="radio" id="one" value="One" v-model="picked" />
      <label for="one">One</label>
      <br />
      <input type="radio" id="two" value="Two" v-model="picked" />
      <label for="two">Two</label>
      <br />
      <span>Picked: {{ picked }}</span>
    </div>
    <div id="v-model-select" class="demo">
      <select v-model="selected">
        <option disabled value="">Please select one</option>
        <option>A</option>
        <option>B</option>
        <option>C</option>
      </select>
      <span>Selected: {{ selected }}</span>
    </div>
    <div>
      <select v-model="selected" multiple>
        <option>A</option>
        <option>B</option>
        <option>C</option>
      </select>
      <br />
      <span>Selected: {{ selected }}</span>
    </div>
    <div id="v-model-select-dynamic" class="demo">
      <select v-model="selected">
        <option
          v-for="option in options"
          :value="option.value"
          :key="option.value"
        >
          {{ option.text }}
        </option>
      </select>
      <span>Selected: {{ selected }}</span>
    </div>
    <div>
      <!-- 当选中时，`picked` 为字符串 "a" -->
      <input type="radio" v-model="picked" value="a" />

      <!-- `toggle` 为 true 或 false -->
      <input type="checkbox" v-model="toggle" />

      <!-- 当选中第一个选项时，`selected` 为字符串 "abc" -->
      <select v-model="selected">
        <option value="abc">ABC</option>
      </select>
    </div>
    <div>
      <input
        type="checkbox"
        v-model="toggle"
        true-value="yes"
        false-value="no"
      />
      <span>toggle: {{ toggle }}</span>
    </div>
    <div>
      <input type="radio" v-model="pick" v-bind:value="a" />
      <span>pick: {{ pick }}</span>
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
      checked: false,
      checkedNames: [],
      picked: "",
      selected: "A",
      options: [
        { text: "One", value: "A" },
        { text: "Two", value: "B" },
        { text: "Three", value: "C" },
      ],
      toggle: false,
      pick: "",
      a: "1",
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
