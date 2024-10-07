<script setup>
import { ref, watch, onMounted } from 'vue';
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
            <slot name="title">
                <h1 class="titleText">在小鎮的午後</h1>
            </slot>
            <span class="material-symbols-outlined closeIcon" @click="closeDialog">
                close
            </span>
            <slot name="content">
                <p class="contentText">
                    在一個寧靜的小鎮上，午後的陽光柔和地灑在街道上。樹影斑駁，微風輕拂，帶來了遠處花香的氣息。小鎮的生活彷彿在這樣的時光中變得緩慢而恬靜。我坐在咖啡館的戶外座位上，手中捧著一杯剛沖好的拿鐵，熱氣緩緩上升，彷彿在與午後的陽光對話。咖啡館裡傳來輕柔的音樂，伴隨著周圍人們的低語聲，讓人感到一種難以言喻的安逸。不遠處，一位老奶奶正在市場上擺攤，手中拿著新鮮的水果和自家種的蔬菜。她的臉上洋溢著微笑，與路過的每一個人打著招呼。小孩們則在街道上追逐嬉鬧，他們的笑聲如同清脆的鈴聲，回蕩在空氣中。這樣的午後，不僅僅是時間的流逝，更是一種生活的享受。我放下咖啡杯，靜靜地看著眼前的一切，心中充滿了對生活的感激。每一個細微的瞬間，都彷彿在告訴我：生活的美好，常常藏在那些不經意的時刻裡。就在這時，一位年輕的畫家走進了我的視線，她手裡拿著畫板，似乎要將眼前的景象捕捉下來。她專注的神情讓我想起了創作的熱情，無論是畫畫、寫作還是其他形式的表達，都是對生活的熱愛。
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