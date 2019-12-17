<template>
  <form v-on:submit.prevent="bookSubmit(bookData)" class="" action="#" method="post">
    <input v-model="bookData.bookTitle" type="text" name="title" value="" placeholder="Book Title">
    <input v-model="bookData.bookAuthor" type="text" name="author" value="" placeholder="Book Author">
    <div>
        <input id="finishedReading" type="checkbox" v-model="bookData.finishedReading"/>
        <label for="finishedReading">Finished Reading</label>
    </div>
    <input id="borrowed" value="borrowed" type="radio" v-model="bookData.ownership" />
    <label for="borrowed">borrowed</label>
    <input id="bought" value="bought" v-model="bookData.ownership" type="radio"/>
    <label for="bought">bought</label>

    <button type="submit" name="button">Add Book</button>
  </form>
</template>

<script>
export default {
  name: "BookForm",
  props: ["books"],
  data() {
    return {
        bookData: {
            bookTitle: "",
            bookAuthor: "",
            finishedReading: false,
            ownership: ""
        }
    };
  },
  methods: {
    bookSubmit(bookData) {
      this.$emit("addBook", bookData);
    }
  }
};
</script>

<style>
</style>
