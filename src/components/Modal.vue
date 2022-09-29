<template>
  <Transition name="modal-outer">
    <div
      v-show="modalOpen"
      class="absolute w-full h-screen bg-opacity-30 px-9 top-0 left-0 flex justify-center"
    >
      <Transition name="modal-outer">
        <div
          v-if="modalOpen"
          class="frosted self-start p-4 mt-32 max-w-screen-md border-solid rounded-lg"
        >
          <slot />
          <button @click="$emit('close-modal')" class="bg-white p-4">
            Close
          </button>
        </div>
      </Transition>
    </div>
  </Transition>
</template>

<script setup>
defineEmits(["close-modal"]);
defineProps({
  modalOpen: {
    type: Boolean,
    default: false,
  },
});
</script>

<style>
.frosted {
  position: relative;
  overflow: hidden;
  width: 70%;
  height: 70%;
  border-radius: 16px;
  z-index: 1;
}

.frosted:before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  margin: -20px;
  box-shadow: inset 0 0 500px rgba(255, 255, 255, 0.4);
  filter: blur(10px);
  z-index: -1;
}

.modal-outer-enter-active,
.modal-outer-leave-active {
  transition: opacity 0.6s cubic-bezier(0.52, 0.02, 0.19, 1.02);
}
.modal-outer-enter-from,
.modal-outer-leave-to {
  opacity: 0;
}

.modal-inner-enter-active {
  transition: all 0.3s cubic-bezier(0.52, 0.02, 0.19, 1.02) 0.15s;
}
.modal-inner-leave-active {
  transition: all 0.3s cubic-bezier(0.52, 0.02, 0.19, 1.02);
}
.modal-inner-enter-from {
  opacity: 0;
  transform: scale(0.8);
}
.modal-inner-leave-to {
  transform: scale(0.8);
}
</style>
