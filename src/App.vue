<template>
  <header>
    <h1>Math Quiz App</h1>
  </header>

  <OperatorQuiz @onBack="clearOperators" v-if="operator" :operator="operator" />
  <OperatorSelector v-if="!operator" @changeOperator="changeOperator" />
</template>

<script>
import OperatorSelector from "./components/OperatorSelector.vue";
import OperatorQuiz from "./components/OperatorQuiz.vue";
import Navbar from "./components/Navbar.vue";
export default {
  name: "App",
  data() {
    return { operator: null };
  },
  methods: {
    changeOperator(operator) {
      this.operator = operator;
    },
    clearOperators() {
      this.operator = null;
    },
  },
  components: { OperatorSelector, OperatorQuiz },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

h1 {
  color: #400040;
  font-weight: italic;
  font-weight: 500;
}
header {
  background-color: #48d1cc;
  top: 0;
  height: 80px;
  display: flex; /* set display to flex */
  justify-content: center; /* center horizontally */
  align-items: center; /* center vertically */
  margin-bottom: 30px;
}
</style>
