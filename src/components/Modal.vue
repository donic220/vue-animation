<template>
  <div class="backdrop" v-if="open"></div>
  <transition name="modal">
    <dialog class="dialog" open v-if="open">
      <slot> </slot>
    </dialog>
  </transition>
</template>

<script setup lang="ts">
type Props = {
  open: boolean;
};

defineProps<Props>();
</script>

<style scoped>
.backdrop {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  z-index: 10;
  background-color: rgba(0, 0, 0, 0.063);
}

.dialog {
  position: fixed;
  top: 30vh;
  width: 30rem;
  left: calc(50% - 15rem);
  margin: 0;
  box-shadow: 0 2px 8px rgbn(0, 0, 0, 0.25);
  border-radius: 12px;
  padding: 1rem;
  background-color: white;
  z-index: 100;
  border: none;
}
.modal-enter-active {
  animation: modal 0.3s ease-out;
}
.modal-leave-active {
  animation: modal 0.3s ease-in reverse;
}

@keyframes modal {
  from {
    opacity: 0;
    transform: translateX(-50px) scale(0.9);
  }

  100% {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}
</style>
