<template>
  <div class="todo-create">
    <input
      type="text"
      placeholder="Create new todo by pressing enter"
      v-model="newTodo"
      @keyup.enter="createNewTodo"
    />
  </div>
</template>

<script setup>
import { ref, defineEmits } from "vue";

// emits
const emit = defineEmits(["new-todo", "error-todo"]);

// todo data
const newTodo = ref("");
const createNewTodo = () => {
  if (newTodo.value !== "") {
    emit("new-todo", newTodo.value);
    newTodo.value = "";
    return;
  }
  emit("error-todo");
};
</script>

<style lang="scss" scoped>
.todo-create {
  input[type="text"] {
    border: 1px solid transparent;
    border-radius: 6px;
    padding: 16px 6px;
    width: 100%;
    box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
    &:focus {
      outline: none;
    }
  }
}
</style>
