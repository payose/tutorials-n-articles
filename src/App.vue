<template>
  <div id="app">
    <h2>Random questions and their answers</h2>
    <div v-for="(question, index) in questions" :key="index">
      <Card :question="question" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Card from "./components/Card";

export default {
  name: "App",
  components: {
    Card,
  },
  data() {
    return {
      questions: [],
    };
  },

  methods: {
    getQuestions() {
      axios
        .get("https://opentdb.com/api.php?amount=5")
        .then((response) => this.questions.push(...response.data.results))
        .catch((error) => console.log(error));
    },

    getMoreQuestions() {
      window.onscroll = () => {
        let bottomOfWindow =
          document.documentElement.scrollTop + window.innerHeight ===
          document.documentElement.offsetHeight;

        if (bottomOfWindow) {
          this.getQuestions();
        }
      };
    },
  },

  mounted() {
    this.getQuestions();
    this.getMoreQuestions();
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: rgb(56, 114, 109);
  margin-top: 60px;
}
</style>
