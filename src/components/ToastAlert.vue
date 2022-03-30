<template>
  <transition name="toast">
    <div v-if="showError" class="toast-alert-wrap">
      <div class="toast-alert">
        <span>Todo cannot be empty!</span>
      </div>
    </div>
  </transition>
</template>

<script setup>
import { defineProps } from "vue";
defineProps({
  showError: Boolean,
});
</script>

<style lang="scss" scoped>
.toast-alert-wrap {
  position: relative;

  .toast-alert {
    width: 100%;
    position: absolute;
    padding: 16px;
    border-radius: 8px;
    box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
    background-color: rgb(181, 4, 4);
    color: #fff;
  }
}

@keyframes shake {
  0% {
    transform: translateY(-100px);
  }
  50% {
    transform: translateY(0);
  }
  60% {
    transform: translateX(-6px);
  }
  70% {
    transform: translateX(0px);
  }
  80% {
    transform: translateX(6px);
  }
  90% {
    transform: translateX(0px);
  }
  100% {
    transform: translateX(-4px);
  }
}

.toast-enter-active {
  animation: shake 0.4s ease;
}

.toast-leave-active {
  transition: 0.4s ease all;
}

.toast-leave-to {
  transform: translateY(-100px);
}
</style>
