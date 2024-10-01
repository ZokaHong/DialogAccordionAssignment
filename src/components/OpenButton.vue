<script setup>
const emit = defineEmits(['open']);

const handleClick = () => {
    emit('open');
};
const props = defineProps({
    openButton: {
        type: String,
        required: true
    }
})

</script>

<template>
    <button class="button-style" :class="openButton" @click="handleClick">
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
    padding: 15px 20px;
    background-color: rgb(29, 171, 218);
    border-radius: 5px;
    cursor: pointer;
}
</style>