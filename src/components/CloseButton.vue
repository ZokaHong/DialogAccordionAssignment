<script setup>
const emit = defineEmits(['close']);

const handleClick = () => {
    emit('close');
};
</script>

<template>
    <button class="button-style" @click="handleClick">
        <slot></slot>
    </button>
</template>

<style scoped>
.button-style {
    display: flex;
    justify-content: center;
    align-items: center;
    width: max-content;
    height: max-content;
    padding: 5px 10px;
    background-color: rgb(250, 201, 208);
    border-radius: 5px;
    cursor: pointer;
}
</style>