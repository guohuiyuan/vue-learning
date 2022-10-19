<template>
  <li>
    {{ title }}
    <button @click="$emit('remove')">Remove</button>
  </li>
</template>

<script>
export default {
  name: "todoitem",
  props: ['title'],
  emits: ['remove'],
};
</script>
