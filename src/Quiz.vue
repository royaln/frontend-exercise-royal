<template>
  <div v-if="index != questions.length">
    <div>
      <div>{{ currentQuestion.text }}</div>
      <div v-for="choice in currentQuestion.answers" v-bind:key="choice">
        <input type="radio" v-model="answer" :value="choice">
        <label for="one">{{ choice }}</label>
      </div>
      <br>
      <span>Picked: {{ index + ":" + questions.length }}</span>
      <span>Picked: {{ questions[index].answer }}</span>
    </div>
    <div>
      <button v-on:click="next" v-bind:disabled="!answer">Next</button>
    </div>
  </div>
  <div v-else>
    <div v-for="(a) in answers" v-bind:key="a">
      <div>{{ a }}</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    questions: {
      type: Array,
      required: true
    }
  },
  methods: {
    next(event) {
      this.answers.push(this.answer);
      this.answer = null;
      this.currentQuestion = this.questions[++this.index];
    }
  },
  data() {
    return {
      index: 0,
      currentQuestion: this.questions[0],
      answer: null,
      answers: []
    };
  }
};
</script>
