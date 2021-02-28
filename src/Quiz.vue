<template>
  <div>
    <div>{{ currentQuestion.text }}</div>
    <div v-for="choice in currentQuestion.answers" v-bind:key="choice">
      <input type="radio" v-model="answers[index]" :value="choice" />
      <label for="one">{{ choice }}</label>
    </div>
    <div>
      <button v-on:click="next" v-bind:disabled="!answers[index]">Next</button>
    </div>
    <div>{{ answers[index - 1] }}</div>
  </div>
</template>

<script>
export default {
  props: {
    questions: {
      type: Array,
      required: true,
    },
  },
  methods: {
    next(event) {
      this.currentQuestion = this.questions[++this.index];
    },
  },
  data() {
    return {
      index: 0,
      currentQuestion: this.questions[0],
      answer: null,
      answers: [],
    };
  },
};
</script>
