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
      <input v-model="message2" />
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
      message2: "hello world"
    };
  },
  methods: {
    reverseMessage() {
      this.message = this.message.split("").reverse().join("");
    },
  },
};
</script>
