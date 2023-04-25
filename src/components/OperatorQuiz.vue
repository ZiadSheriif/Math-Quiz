<template>
  <div>
    <div v-if="isQuizStarted">
      <div>{{ operandLeft }} {{ operator }} {{ operandRight }}</div>
      <button
        @click="selectAnswer(answer)"
        v-for="(answer, index) of answers"
        :key="index"
      >
        {{ answer }}
      </button>
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

      const calculateAnswer = {
        "+": (a, b) => a + b,
        "-": (a, b) => a - b,
        "*": (a, b) => a * b,
        "/": (a, b) => a / b,
      };

      const methodUsed = calculateAnswer[this.operator];

      this.answers = [];
      this.answers.push(
        methodUsed(
          this.operandLeft * Math.floor(Math.random() * 10),
          this.operandRight + 1
        )
      );
      this.answers.push(
        methodUsed(this.operandLeft + 1, this.operandRight) *
          Math.floor(Math.random() * 10)
      );
      this.answers.push(
        methodUsed(
          this.operandLeft * Math.floor(Math.random() * 10),
          this.operandRight * Math.floor(Math.random() * 10)
        )
      );
      this.answers.push(
        methodUsed(
          this.operandLeft * Math.floor(Math.random() * 10),
          this.operandRight * Math.floor(Math.random() * 10)
        )
      );
      this.answers.push(
        methodUsed(
          this.operandLeft * Math.floor(Math.random() * 10),
          this.operandRight - 2
        )
      );

      const expectedAnswer = methodUsed(this.operandLeft, this.operandRight);
      this.answers[parseInt(Math.random() * this.answers.length)] = expectedAnswer;
      this.expectedAnswer = expectedAnswer;
    },

    selectAnswer(answerSelected) {
      if (answerSelected !== this.expectedAnswer) {
        alert("WRONG ANSWER");
      }
      this.startQuiz();
    },
  },
};
</script>

<style></style>
