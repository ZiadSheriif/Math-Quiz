<template>
  <div class="button-box">
    <button @click="$emit('changeOperator', '+')">Addition (+)</button>
    <button @click="$emit('changeOperator', '-')">Subtraction (-)</button>
    <button @click="$emit('changeOperator', '*')">Multiplication (*)</button>
    <button @click="$emit('changeOperator', '/')">Division (/)</button>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return { operator: null };
  },
  methods: {
    selectOperator(operator) {
      this.operator = operator;
    },
  },
};
</script>

<style>
button {
  color: #116ecb;
  background-color: #00ffff;
  flex-direction: row;
  align-items: center;
  text-align: center;
  border: #00ffff;
  margin: 5px;
  width: 120px;
  height: 100px;
  cursor: pointer;
}
button:hover {
  border: #0000;
}
.button-box {
  display: flex;
  text-align: center;
  align-items: center;
  justify-content: center;
}
</style>
