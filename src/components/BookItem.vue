<template>
  <div>
    <ul>
      <li>
        <img width="30%" height="30%" src="../assets/book-icon.png" />
        <h3>{{ book.title }}</h3>
        <p>
          {{ book.description }}
        </p>
        <p>Published on: {{ new Date(book.publishDate).toDateString() }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "BookItem",
  props: ["book"],
  methods: {}
};
</script>

<style scoped>
.book-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}
* {
  margin: 0;
  padding: 0;
}

div {
  margin: 20px;
}

ul {
  list-style-type: none;
  width: 500px;
}

h3 {
  font: bold 20px/1.5 Helvetica, Verdana, sans-serif;
}

li img {
  float: left;
  margin: 0 15px 0 0;
}

li p {
  margin: 0 0 10px 0;
}

li {
  padding: 10px;
  overflow: auto;
}

li:hover {
  background: #eee;
  cursor: pointer;
}
</style>
