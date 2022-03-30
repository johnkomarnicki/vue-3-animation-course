<template>
  <ul v-if="todos.length > 0">
    <li v-for="todo in todos" :key="todo.id" class="todo">
      <span>{{ todo.todo }}</span>
      <i @click="$emit('remove-todo', todo)" class="fa-solid fa-xmark"></i>
    </li>
  </ul>
  <p v-else>Awesome, you completed all your todos!</p>
</template>

<script setup>
import { defineProps } from "vue";
defineProps({
  todos: Array,
});
</script>

<style lang="scss" scoped>
ul {
  margin-top: 24px;
  border-radius: 10px;
  position: relative;

  .todo {
    width: 100%;
    padding: 16px 6px;
    display: flex;
    align-items: center;
    background-color: #fff;
    color: #000;
    border-radius: 8px;
    margin-bottom: 20px;
    box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);

    span {
      flex: 1;
    }

    i {
      color: #000;
      opacity: 0;
      margin-right: 8px;
      font-size: 20px;
      align-self: flex-end;
    }

    &:hover {
      i {
        opacity: 1;
      }
    }
  }
}

p {
  margin-top: 24px;
  text-align: center;
}
</style>
