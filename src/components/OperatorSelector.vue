//? $emit To emit an event from the child component
<template>
  <div class="button-box">
    <button @click="$emit('changeOperator', '+')">Addition <br />+</button>
    <button @click="$emit('changeOperator', '-')">Subtraction <br />-</button>
    <button @click="$emit('changeOperator', '*')">Multiplication <br />*</button>
    <button @click="$emit('changeOperator', '/')">Division <br />/</button>
  </div>
</template>

<script>
export default {};
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
button:hover,
:focus {
  border: #0000;
}
.button-box {
  display: flex;
  text-align: center;
  align-items: center;
  justify-content: center;
}
</style>
