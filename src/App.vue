<script setup>
import Dialog from './components/Dialog.vue';
import Accordions from './components/Accordions.vue';
</script>

<template>
  <div class="container">
    <Dialog />
    <Accordions />
  </div>


</template>

<style scoped>
.container{
  position: absolute;
  top: 10%;
  left: 20%;
  display: grid;
  grid-template: 100px 1fr / 300px;
  justify-content: flex-start;
  align-content: flex-start;
}

</style>
