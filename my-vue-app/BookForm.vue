<template>
    <form @submit.prevent="submitForm">
      <input v-model="book.title" type="text" placeholder="Название книги">
      <input v-model="book.author" type="text" placeholder="Автор">
      <button type="submit">Сохранить</button>
    </form>
  </template>
  
  <script>
  export default {
    data() {
      return {
        book: {
          id: null,
          title: '',
          author: '',
        },
      };
    },
    methods: {
      submitForm() {
        if (this.book.id) {
          // Редактирование книги
          this.$emit('edit', this.book);
        } else {
          // Добавление новой книги
          this.$emit('add', this.book);
        }
        this.resetForm();
      },
      resetForm() {
        this.book = {
          id: null,
          title: '',
          author: '',
        };
      },
    },
  };
  </script>