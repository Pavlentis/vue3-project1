<template>
    <div>
      <h1>Управление книгами</h1>
      <BookForm @add="addBook" @edit="editBook" :book="editedBook" />
      <BookList :books="books" @edit="startEdit" @delete="deleteBook" />
    </div>
  </template>
  
  <script>
  import { books } from './data.js';
  import BookForm from './components/BookForm.vue';
  import BookList from './components/BookList.vue';
  
  export default {
    components: { BookForm, BookList },
    data() {
      return {
        books: books,
        editedBook: null,
      };
    },
    methods: {
      addBook(newBook) {
        newBook.id = this.books.length + 1;
        this.books.push(newBook);
      },
      startEdit(book) {
        this.editedBook = { ...book };
      },
      editBook(editedBook) {
        const index = this.books.findIndex((book) => book.id === editedBook.id);
        if (index !== -1) {
          this.books[index] = editedBook;
        }
        this.editedBook = null;
      },
      deleteBook(id) {
        this.books = this.books.filter((book) => book.id !== id);
      },
    },
  };
  </script>