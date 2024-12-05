<template>
    <ul>
      <li v-for="book in books" :key="book.id">
        {{ book.title }} ({{ book.author }})
        <button @click="$emit('edit', book)">Редактировать</button>
        <button @click="$emit('delete', book.id)">Удалить</button>
      </li>
    </ul>
  </template>
  
  <script>
  export default {
    props: {
      books: {
        type: Array,
        required: true,
      },
    },
  };
  </script>