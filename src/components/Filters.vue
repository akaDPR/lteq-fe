<template>
  <div>
    <h3>
      Filters
    </h3>
    {{ selectedDate }}
    <div class="filter">
      <h3>Select a date</h3>
      <Datepicker
        v-model="selectedDate"
        :calendarButton="true"
        :clearButton="true"
        @cleared="resetAll()"
        @input="dateFilter(selectedDate)"
      ></Datepicker>
    </div>
    <div>
      <label for="searchTitle">
        Search by book title
        <input
          type="text"
          id="searchTitle"
          v-model="searchTerm"
          @keypress.enter="searchTitle(searchTerm)"
        />
      </label>
      <button v-on:click="resetAll()">Reset</button>
    </div>
  </div>
</template>

<script>
import Datepicker from "vuejs-datepicker";

export default {
  name: "Filters",
  components: {
    Datepicker
  },
  props: ["searchTitle", "resetAll", "dateFilter"],
  data() {
    return {
      searchTerm: "",
      selectedDate: ""
    };
  },
  methods: {}
};
</script>

<style scoped>
.filter {
  width: 50%;
  padding: 60px;
  margin: 0 257px auto;
}
</style>
