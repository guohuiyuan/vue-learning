<template>
  <div class="blogpost">
    <h4>{{ title }}</h4>
    <button @click="$emit('enlarge-text', 0.1)">Enlarge text</button>
  </div>
</template>

<script>
export default {
  name: "blogpost",
  props: ["title"],
  emits: ["enlarge-text"],
};
</script>
