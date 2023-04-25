<template>
  <div>
    <div v-if="isQuizStarted">
      <div>{{ operandLeft }}{{ operator }} {{ operandRight }}</div>
      <button v-for="(answer, index) of answers" :key="index">{{ answer }}</button>
    </div>
    <div v-if="!isQuizStarted">
      <button @click="startQuiz">Start</button>
    </div>
    <button @click="$emit('onBack')">Back</button>
  </div>
</template>

<script>
export default {
  props: ["operator"],

  data() {
    return {
      operandRight: null,
      operandLeft: null,
      isQuizStarted: false,
      answers: [],
      expectedAnswer: null,
    };
  },

  methods: {
    startQuiz() {
      this.operandLeft = parseInt(Math.random() * 13);
      this.operandRight = parseInt(Math.random() * 13);
      this.isQuizStarted = true;
      for (let i = 0; i < 5; i++) {
        const answer =
          this.operandRight * parseInt(Math.random() * 4) +
          this.operandLeft * parseInt(Math.random() * 4);
        this.answers.push(answer);
      }
    },
  },
};
</script>

<style></style>
