<template>
  <div class="view">
    <ToastAlert :showError="showError" />
    <div class="view-header">
      <h1>Create Todo</h1>
      <span>With Vue Animations</span>
    </div>
    <CreateTodo @new-todo="newTodo" @error-todo="errorTodo" />
    <TodosList :todos="todos" @remove-todo="removeTodo" />
  </div>
</template>

<script setup>
import { uid } from "uid";
import { ref } from "vue";
import CreateTodo from "@/components/CreateTodo.vue";
import TodosList from "@/components/TodosList.vue";
import ToastAlert from "@/components/ToastAlert.vue";

// todo data
const todos = ref([
  { todo: "take out the garbage", id: uid() },
  { todo: "do the dishes", id: uid() },
]);

const newTodo = (payload) => {
  todos.value.unshift({
    todo: payload,
    id: uid(),
  });
};

const showError = ref(null);
const errorTodo = () => {
  showError.value = true;
  setTimeout(() => {
    showError.value = null;
  }, 2500);
};

const removeTodo = (payload) => {
  todos.value = todos.value.filter((todo) => todo.id !== payload.id);
};
</script>

<style lang="scss" scoped>
.view {
  max-width: 450px;
  margin: 0 auto;
  padding: 32px 16px;

  &-header {
    margin-bottom: 32px;
  }
}
</style>
