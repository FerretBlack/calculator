<template>
  <div :class="$style.wrapper">
    {{ expression }}
  </div>
</template>

<script setup>
defineProps({
  expression: {
    type: [String, Number],
    default: 0
  },
});
</script>

<style lang="scss" module>
  .wrapper {
    background: #7C7C7C;
    width: 100%;
    font-size: 25px;
    padding: 18px;
    text-align: end;
    color: white;
  }
</style>>