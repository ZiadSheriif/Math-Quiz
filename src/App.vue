<template>
  <header><h1 class="header">Math Quiz App</h1></header>
  <OperatorSelector @changeOperator="changeOperator" />
</template>

<script>
import OperatorSelector from "./components/OperatorSelector.vue";
export default {
  name: "App",
  data() {
    return { operator: null };
  },
  methods: {
    changeOperator(operator) {
      this.operator = operator;
    },
  },
  components: { OperatorSelector },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  color: #400040;
  font-weight: italic;
  font-weight: 500;
}
</style>
