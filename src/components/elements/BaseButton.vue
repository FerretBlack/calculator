<template>
  <button :class="$style['base-button']">
    {{ title }}
  </button>
</template>

<script setup>
defineProps({
  title: {
    type: [String, Number],
    required: true,
  },
});
</script>

<style lang="scss" module>
.base-button {
  display: inline-block;
  border: none;
  padding: 1rem 2rem;
  margin: 0;
  text-decoration: none;
  font-family: Roboto, Arial, sans-serif;
  color: white;
  line-height: 1;
  cursor: pointer;
  text-align: center;

  &:hover {
    box-shadow: 0px 0px 20px 3px rgba(97, 97, 97, 0.25);
  }
}
</style>