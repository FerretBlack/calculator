<template>
  <div :class="$style.wrapper">
    <InputWrapper :expression="expression" :class="$style.input" />
    <div :class="$style.container">
      <ButtonGroup @set-value="setValue" />
      <History :operations="operations" :class="$style.history" />
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import InputWrapper from "./components/InputWrapper.vue";
import ButtonGroup from "./components/ButtonGroup.vue";
import History from "./components/History.vue";

const expression = ref(0);
const operations = ref([]);
const operators = ref(["+", "-", "/", "*"])

const getAnswer = () => {
  if (typeof expression.value !== "string") {
    return;
  }

  const operation = expression.value;
  const exp = eval(expression.value.replace(/ /g, ""));

  if (expression.value != exp) {
    expression.value = exp;
    operations.value.push(`${operation} = ${exp}`);
  }
};

const setValue = (event) => {
  if (event === "drop") {
    expression.value = 0;
    return;
  }

  if (event === "delete") {
    if (expression.value) {
      expression.value = expression.value.trim();
      expression.value =
        expression.value.length > 1
          ? expression.value
              .substr(0, expression.value.length - 1)
              .replace(/ /g, "")
          : 0;
    } else {
      expression.value = 0;
    }

    return;
  }

  if (operators.value.includes(event)) {
    if (operators.value.includes(expression.value.toString().replace(/ /g, "").slice(-1))) {
      return;
    }
    expression.value = expression.value += ` ${event} `;
    return;
  }

  if (event === "enter") {
    getAnswer();
    return;
  }

  if (expression.value) {
    expression.value += String(event);
  } else {
    expression.value = event;
  }
};
</script>

<style lang="scss" module>
.wrapper {
  background: #e7e7e7;
  padding: 40px;
  border-radius: 10px;

  @media screen and (max-width: 500px) {
    padding: 20px;
  }
}

.container {
  display: flex;
}

.history {
  flex-shrink: 2;

  @media screen and (max-width: 1135px) {
    display: none;
  }
}

.input {
  margin-bottom: 20px;
}
</style>
