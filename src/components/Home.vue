<template>
  <div id="app" class="container">
    <div class="splitArea">
      <Filters
        :searchTitle="searchTitle"
        :resetAll="resetAll"
        :dateFilter="dateFilter"
      />
    </div>
    <div class="splitArea">
      <BookList v-bind:books="books" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import BookList from "../components/BookList.vue";
import Filters from "../components/Filters.vue";
export default {
  name: "Home",
  components: {
    BookList,
    Filters
  },
  data() {
    return {
      books: []
    };
  },

  methods: {
    dateFilter(selectedDate) {
      this.books = this.books.filter(
        el =>
          new Date(el.publishDate).setHours(0, 0, 0, 0) ===
          new Date(selectedDate).setHours(0, 0, 0, 0)
      );
    },
    searchTitle(title) {
      if (!title.length) return;
      this.books = this.books.filter(el =>
        el.title.toLowerCase().includes(title.toLowerCase())
      );
    },
    resetAll() {
      this.collectAll();
    },
    async collectAll() {
      this.books = await axios(
        `https://fakerestapi.azurewebsites.net/api/v1/Books`
      ).then(res => res.data);
    }
  },

  created() {
    this.collectAll();
  }
};
</script>

<style scoped>
.container {
  display: flex;
  margin: 20px;
}
.splitArea {
  width: 40%;
}
</style>
