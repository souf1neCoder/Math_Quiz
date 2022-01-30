<template>
  <div class="container mt-5">
    <div v-if="isStart">
      <h4 class="opr">{{ operandLeft }} {{ operator }} {{ operandRight }}</h4>
      <div class="anwers mb-5">
        <button
          class="answers-btns btn btn-dark"
          @click="selectedAnswer(answer)"
          v-for="(answer, index) of answers"
          :key="index"
        >
          {{ answer }}
        </button>
      </div>
    </div>
    <div v-if="end">
      <img
        v-if="score <= 3"
        src="https://www.smileysapp.com/gif-emoji/thumbs-down.gif"
        alt="scoreEmoji"
      />
      <img
        v-if="score > 3 && score <= 6"
        src="https://www.smileysapp.com/gif-emoji/coffee.gif"
        alt="scoreEmoji"
      />
      <img
        v-if="score > 6 && score <= 9"
        src="https://www.smileysapp.com/gif-emoji/thumbs-down.gif"
        alt="scoreEmoji"
      />
      <img
        v-if="score > 9 && score <= 12"
        src="https://www.smileysapp.com/gif-emoji/deal-with-it.gif"
        alt="scoreEmoji"
      />
      <h2 class="opr">Your Score is {{ score }}</h2>
    </div>
    <div v-if="!isStart">
      <button class="btn btn-primary mb-5" @click="startQuiz">Start</button>
    </div>
    <button class="btn btn-secondary" @click="$emit('onBack')">Back</button>
  </div>
</template>

<script>
export default {
  props: ["operator"],
  data() {
    return {
      isStart: false,
      operandLeft: null,
      operandRight: null,
      answers: [],
      expectedAnswer: null,
      score: 0,
      questions: [],
      end: false,
    };
  },
  methods: {
     getRandomArbitrary(min, max) {
    return Math.random() * (max - min) + min;
},
    selectedAnswer(selected) {
      if (this.questions.length === 0) {
        this.score = 0;
      }
      if (selected === this.expectedAnswer) {
        this.score++;
      }

      this.questions.push(selected);
      this.answers = [];
      this.startQuiz();
      if (this.questions.length > 11) {
        this.isStart = !this.isStart;
        this.end = !this.end;
        this.questions = [];
      }
    },
    startQuiz() {
      if (this.end === true) {
        this.end = false;
      }
      this.isStart = true;

      this.operandLeft = parseInt(Math.random() * 17);
      this.operandRight = parseInt(Math.random() * 17);
      const methods = {
        "+": (a, b) => a + b,
        "/": (a, b) => a / b,
        "-": (a, b) => a - b,
        "*": (a, b) => a * b,
      };
      const methodToUse = methods[this.operator];
      while (this.answers.length < 5) {
        const answer = parseInt(this.getRandomArbitrary(-100,100));
        this.answers.push(answer);
        this.answers = [...new Set(this.answers)];
      }
      const expectedAnswer = methodToUse(this.operandLeft, this.operandRight);
      this.answers[
        parseInt(Math.random() * this.answers.length)
      ] = expectedAnswer;
      this.expectedAnswer = expectedAnswer;
    },
  },
};
</script>

<style scoped>
.opr {
  font-weight: bold;
  font-size: 1.6rem;
  margin-bottom: 40px;
  letter-spacing: 5px;
}

</style>
