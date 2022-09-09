<template>
  <div :class="$style.wrapper">
    <h3 :class="$style.title">Журнал</h3>

    <p v-if="!operations">Журнал операций пуст</p>
    <div v-else>
      <p v-for="operation of operations" :key="operation">
        {{ operation }}
      </p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  operations: {
    type: Array,
    default: null,
  },
});
</script>

<style lang="scss" module>
.wrapper {
  width: 100%;
  padding: 0 15px;
}

.title {
  font-weight: 700;
}
</style>