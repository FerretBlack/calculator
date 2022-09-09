<template>
  <div :class="$style.wrapper">
    <BaseButton
      v-for="(button, index) of buttons"
      :key="index"
      :class="[
        $style.button,
        { [$style['-operator']]: button.type === 'operator' },
      ]"
      @click="$emit('setValue', button.value)"
      :title="button.label"
    />
  </div>
</template>

<script setup>
import { reactive } from "vue";
import BaseButton from "../components/elements/BaseButton.vue";

const buttons = reactive([
  {
    label: "%",
    type: "operator",
  },
  {
    label: "CE",
    type: "operator",
  },
  {
    label: "C",
    type: "operator",
    value: "drop",
  },
  {
    label: "⌫",
    type: "operator",
    value: "delete",
  },
  {
    label: 1,
    type: "number",
    value: 1,
  },
  {
    label: 2,
    type: "number",
    value: 2,
  },
  {
    label: 3,
    type: "number",
    value: 3,
  },
  {
    label: "÷",
    type: "operator",
    value: "/",
  },
  {
    label: 4,
    type: "number",
    value: 4,
  },
  {
    label: 5,
    type: "number",
    value: 5,
  },
  {
    label: 6,
    type: "number",
    value: 6,
  },
  {
    label: "×",
    type: "operator",
    value: "*",
  },
  {
    label: 7,
    type: "number",
    value: 7,
  },
  {
    label: 8,
    type: "number",
    value: 8,
  },
  {
    label: 9,
    type: "number",
    value: 9,
  },
  {
    label: "−",
    type: "operator",
    value: "-",
  },
  {
    label: ",",
    type: "operator",
  },
  {
    label: 0,
    type: "number",
    value: 0,
  },
  {
    label: "+",
    type: "operator",
    value: "+",
  },
  {
    label: "=",
    type: "operator",
    value: "enter",
  },
]);
</script>

<style lang="scss" module>
.wrapper {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 16px;
  width: 100%;
}
.button {
  background: #d9d9d9;
  padding: 16px 20px;
  font-size: 32px;
  color: black;
  touch-action: manipulation;

  &.-operator {
    background: #42b883;
    color: white;
  }

  @media screen and (max-width: 500px) {
    font-size: 16px;
  }

  @media screen and (max-width: 320px) {
    padding: 12px 16px;
  }
}
</style>
