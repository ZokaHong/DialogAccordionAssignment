<script setup>
import { ref, watch, onMounted } from 'vue';
const defaultText = {
    title: 'Default Title',
    content: 'Default Content'
}
const props = defineProps({
    modelValue: {
        type: Boolean,
        required: true
    }
})
const dialog = ref(null)

const emit = defineEmits(['update:modelValue'])
const closeDialog = () => {
    emit('update:modelValue', false)
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

</script>

<template>
    <dialog ref="dialog" @click.self="closeDialog">
        <section>
            <h1 class="titleText">
                <slot name="title">
                    {{ defaultText.title }}
                </slot>
            </h1>
            <span class="material-symbols-outlined closeIcon" @click="closeDialog">
                close
            </span>
            <p class="contentText">
                <slot name="content">
                    {{ defaultText.content }}
                </slot>
            </p>
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


.closeIcon {
    font: 700 45px 'Material Symbols Outlined';
    color: brown;
    cursor: pointer;
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