<script setup>
import { ref, watch, onMounted } from 'vue';
const props = defineProps({
    visible: {
        type: Boolean,
        required: true
    }
})
const dialog = ref(null)
onMounted(() => {
    if (props.visible == true) {
        dialog.value.showModal();
    }
});

watch(() => props.visible, (newValue) => {
    if (newValue == true) {
        console.log(newValue)
        dialog.value.showModal()
    } else {
        console.log(newValue)
        dialog.value.close()
    }
})


</script>

<template>
    <dialog ref="dialog">
        <section>
            <slot name="title"></slot>
            <slot name="close"></slot>
            <slot name="content"></slot>
        </section>
    </dialog>
</template>

<style scoped>
dialog {
    padding: 0;
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
</style>