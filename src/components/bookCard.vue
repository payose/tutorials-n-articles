<template>
  <div>
    <div class="book-container">
      <h2>{{ book.title }}</h2>
      <small>by {{ book.author }}</small>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    book: Object,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.book-container {
  border: 1px solid black;
  margin: 10px;
  width: 45%;
  float: left;
}

.book-container h2 {
  color: rgb(201, 101, 29);
}

.book-container small {
  color: #505050;
}
</style>

