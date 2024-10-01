<script setup>

</script>

<template>
    <div id="detailList">
        <details>
            <summary>
                <slot name="title"></slot>
            </summary>
            <slot name="content"></slot>
        </details>
    </div>

</template>

<style scoped>
#detailList {
    width: 400px;
    text-align: start;
    border: 1px solid #000;

}

summary {
    user-select: none;
    cursor: s-resize;
    position: relative;
    padding: 20px 30px;
}

summary::marker {
    content: none;
}

summary::after {
    content: '👉';
    font: 700 22px '';
    position: absolute;
    top: 21px;
    right: 25px;
    transition: .3s;
}

details[open] summary::after {
    transform: rotate(90deg);
}

</style>
