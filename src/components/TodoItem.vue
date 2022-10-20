<template>
  <li>
    {{ title }}
    <button @click="$emit('remove')">Remove</button>
  </li>
</template>

<script>
export default {
  name: "todo-item",
  props: ['title'],
  emits: ['remove'],
};
</script>
