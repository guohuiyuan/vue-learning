<template>
  <input
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  />
</template>

<script>
export default {
  name: "custominput",
  props: ["modelValue"],
  emits: ["update:modelValue"],
};
</script>
