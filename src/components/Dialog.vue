<script setup>
import { nextTick, ref } from 'vue';
const myDialog = ref(null)

const openDialog = () => {
    myDialog.value.showModal()
}
const closeDialog = () => {
    myDialog.value.close()
}

</script>

<template>
    <div role="dialogOpenButton" @click="openDialog" id="openDialog">
        <span>開啟 Dialog</span>
        <span class="material-symbols-outlined openIcon">dialogs</span>
    </div>

    <dialog ref="myDialog">
        <section>
            <h2>Dialog Title</h2>
            <span role="dialogCloseButton" class="material-symbols-outlined closeIcon" @click="closeDialog">
                close
            </span>
            <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Amet nostrum nemo beatae earum sed repellendus soluta dolorem delectus et ducimus, exercitationem voluptas fuga, omnis aliquid officia deserunt? Repudiandae error doloribus tenetur fugiat? Ratione sint hic pariatur corporis amet consequuntur temporibus? Maiores, dolorem sed inventore nobis necessitatibus quos sunt molestiae soluta. Quam nobis necessitatibus optio, explicabo nostrum itaque autem ullam, distinctio, molestias eius possimus iste repudiandae iure sapiente odio est? Dolorum dicta iste id quibusdam, maiores omnis pariatur veritatis sunt suscipit. Suscipit sunt magni nemo, tempore libero consectetur adipisci. Harum ipsum quam natus tempore autem odio dignissimos? Cumque aliquid eveniet dolor!</p>
        </section>
    </dialog>
</template>

<style scoped>
#openDialog{
    width: 150px;
    height: 50px;
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    font: 700 24px '';
    cursor: pointer;
}
dialog::backdrop {
    background-color: rgba(214, 150, 150, 0.2);
}

.closeIcon {
    font: 700 45px 'Material Symbols Outlined';
    color: brown;
    cursor: pointer;
}


section {
    display: grid;
    grid-template: minmax(20px, 60px) 300px / 1fr minmax(20px, 50px);
    /* grid-template-rows: minmax(20px, 60px) 1fr;
    grid-template-columns: 1fr minmax(20px, 50px); */
    align-items: center;
    gap: 10px;
}
section>h2{
    font-family: '';
}

dialog section>p {
    grid-area: 2/1/span 1/ span 2;
    color: rgb(14, 37, 37);
    line-height: 40px;
    align-self: flex-start;
    border-top: 2px solid #000;
}
</style>