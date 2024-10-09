<script setup>
import { ref, watch } from 'vue'

defineProps({
  dialogData: {
    type: Object,
    default: () => {
      return {
        title: 'Default Dialog Title',
        content: 'Default Dialog Content',
      }
    },
  },
})

const dialogVisible = defineModel()

const dialog = ref(null)

function closeDialog() {
  dialogVisible.value = false
}

watch(dialogVisible, (newValue) => {
  if (newValue) {
    dialog.value.showModal()
  }
  else {
    dialog.value.close()
  }
})
</script>

<template>
  <dialog ref="dialog" @click.self="closeDialog">
    <section>
      <slot name="title">
        <h1 class="titleText">
          {{ dialogData.title }}
        </h1>
      </slot>
      <slot name="close" :close-handle="closeDialog">
        <span class="material-symbols-outlined closeIcon">
          close
        </span>
      </slot>
      <slot name="content">
        <p class="contentText">
          {{ dialogData.content }}
        </p>
      </slot>
    </section>
  </dialog>
</template>

<style scoped>
dialog {
  padding: 0;
  background-color: aliceblue;
}

dialog::backdrop {
  background-color: rgba(112, 104, 104, 0.3);
}

section {
  display: grid;
  grid-template: 100px 1fr/ 1fr 100px;
  justify-items: center;
  align-items: center;
  text-align: start;
  gap: 2px;
}

section {
  padding: 5px 15px;
}

.titleText {
  color: chocolate;
}

.closeIcon {
  font: 700 45px 'Material Symbols Outlined';
  color: brown;
  cursor: pointer;
}

.contentText {
  padding: 15px 5px 15px 10px;
  margin: 0 15px;
  border-top: 1px dotted #000;
  font: 400 20px '';
  color: rgb(57, 28, 28);
  grid-area: 2/1/span 1/span 2;
}
</style>
