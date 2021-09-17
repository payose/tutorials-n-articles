<template>
  <div class="card">
    <small class="card-header"
      >category: {{ question.category }}
      <span>difficulty: {{ question.difficulty }}</span></small
    >
    <p>{{ computedQuestion }}</p>
    <small class="card-answer"
      >answer: <span>{{ question.correct_answer }}</span></small
    >
  </div>
</template>

<script>
export default {
  props: {
    question: Object,
  },
  computed: {
    computedQuestion() {
      return this.question.question
        .replace(/&quot;/g, '"')
        .replace(/&#039;/g, "'");
    },
  },
};
</script>

<style>
.card {
  /* border: 1px solid grey; */
  margin: 20px;
  padding: 15px;
  color: rgb(146, 112, 87);
  background-color: rgba(228, 240, 239, 0.753);
  border-radius: 5px;
}

.card p {
  line-height: 2;
  font-weight: bold;
}

.card small {
  color: rgb(175, 153, 139);
}

.card .card-header {
  display: flex;
  padding: 0 20px 20px 20px;
  margin: 0 -20px;
  justify-content: space-between;
  border-bottom: 2px solid rgb(250, 250, 250);
}

.card .card-answer {
  padding: 5px;
}
</style>