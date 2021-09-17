<template>
  <div id="app">
    <h2>infinite screll</h2>
    <input v-model="search" placeholder="search for book by title or arthur" />
    <div v-for="result in searchResults" :key="result.title">
      <bookCard :book="result" :search="search" />
    </div>
  </div>
</template>

<script>
import bookCard from "./components/bookCard";

export default {
  name: "App",
  components: {
    bookCard,
  },
  data() {
    return {
      search: "",
      books: [
        { title: "A time to kill", author: "Josh Grisham" },
        { title: "Greenlights", author: "Matthew McConaughey" },
        { title: "The Da Vinci code", author: "Dan Brown" },
        { title: "Born a crime", author: "Trevor Noah" },
        { title: "The artist way", author: "Julia Cameron" },
        { title: "The hate you give", author: "Angie Thomas" },
        { title: "Billy Summers", author: "Stephen King" },
        { title: "The Kite Runner", author: "Khaled Hosseini" },
      ],
    };
  },

  computed: {
    searchResults() {
      return this.books.filter(
        (books) =>
          books.title.toLowerCase().includes(this.search.toLowerCase()) ||
          books.author.toLowerCase().includes(this.search.toLowerCase())
      );
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 30px;
}

input {
  height: 2em;
  width: 30em;
  padding: 1px 7px;
  font-size: 1em;
  margin-bottom: 12px;
}
</style>
