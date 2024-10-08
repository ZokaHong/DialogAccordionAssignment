<script setup>
import { ref, watch, onMounted } from 'vue';

const dialogVisible = defineModel()

/*
defineModel() 雙向綁定 相當於 props + emit
const props = defineProps({
    modelValue: {
        type: Boolean,
        required: true
    },)}
const emit = defineEmits(['update:modelValue'])
const closeDialog = () => {
    emit('update:modelValue', false)
}
*/

const props = defineProps({
    dialogData: {
        type: Object,
        default: () => {
            return {
                title: 'Default Dialog Title',
                content: 'Default Dialog Content'
            }
        }
    }
})
const dialog = ref(null)

const closeDialog = () => {
    dialogVisible.value = false
}

onMounted(() => {
    if (props.modelValue) {
        dialog.value.showModal();
    }
});

watch(() => props.modelValue, (newValue) => {
    if (newValue) {
        dialog.value.showModal()
    } else {
        dialog.value.close()
    }

})

const closeIconStyle = {
    font: " 700 45px 'Material Symbols Outlined'",
    color: "brown",
    cursor: "pointer"
}

</script>

<template>
    <dialog ref="dialog" @click.self="closeDialog">
        <section>
            <slot name="title">
                <h1 class="titleText">
                    {{ dialogData.title }}
                </h1>
            </slot>
            <slot name="close" :closeIcon="closeIconStyle">
                <span class="material-symbols-outlined" :style="closeIconStyle" @click="closeDialog">
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

.contentText {
    padding: 15px 5px 15px 10px;
    margin: 0 15px;
    border-top: 1px dotted #000;
    font: 400 20px '';
    color: rgb(57, 28, 28);
    grid-area: 2/1/span 1/span 2;
}
</style>