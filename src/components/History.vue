<template>
  <div :class="$style.wrapper">
    <h3 :class="$style.title">Журнал</h3>

    <p v-if="!operations.length" :class="$style.operation">Журнал операций пуст</p>
    <div v-else>
      <p v-for="operation of operations" :key="operation" :class="[$style.operation, $style['-not-empty']]">
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
}

.title {
  font-weight: 700;
  line-height: 1;
}

.operation {
  margin-top: 10px;

  &.-not-empty {
    cursor: pointer;
  }
}
</style>