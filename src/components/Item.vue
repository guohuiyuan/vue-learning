<template>
    <li>{{ todo.text }}</li>
</template>

<script>
export default {
  name: "Item",
  props: {
    todo: String,
  },
  data() {
    return {
      count: 0,
    };
  },
};
</script>