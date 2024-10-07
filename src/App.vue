<script setup>
import Accordions from './components/Accordions.vue';
import Dialog from './components/Dialog.vue'
import { ref } from 'vue';

const dialogVisible = ref(false)


</script>

<template>
  <div class="container">
    <button class="openDialogButton" @click="dialogVisible = true">
      <span>開啟 Dialog</span>
      <span class="material-symbols-outlined openIcon">dialogs</span>
    </button>

    <Dialog v-model="dialogVisible">
      <template #title></template>
      <template #content></template>
    </Dialog>



    <Accordions>
      <template #title={title}>
        {{ title }}
      </template>
      <template #content="{ content }">
        {{ content }}
      </template>
    </Accordions>
  </div>
</template>

<style scoped>
.container {
  position: absolute;
  top: 10%;
  left: 20%;
  display: grid;
  grid-template: 100px 1fr / 600px;
  justify-content: flex-start;
  align-content: flex-start;
}

.openButton {
  color: rgb(250, 250, 250);
  font: 700 32px '';
}

.openButton .openIcon {
  font-size: 36px;
  padding-left: 20px;
}

.openDialogButton {
  display: flex;
  justify-content: center;
  align-items: center;
  width: max-content;
  height: max-content;
  padding: 15px 20px;
  background-color: rgb(29, 171, 218);
  border-radius: 5px;
  cursor: pointer;
}
</style>
