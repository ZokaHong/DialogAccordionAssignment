<script setup>
// eslint-disable-next-line no-unused-vars
const props = defineProps({
    detailData: {
        type: Object,
        default: () => {
            return {
                title: 'Default Accordions Title',
                content: 'Default Accordions Content'
            }
        }
    }
})

</script>

<template>
    <div id="detailList">
        <details>
            <summary>
                <slot name="title">
                    <span class="summaryText">
                        {{ detailData.title }}
                    </span>
                </slot>
            </summary>
            <slot name="content">
                <p class="detailText">{{ detailData.content }}</p>
            </slot>
        </details>
    </div>

</template>

<style>
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


.summaryText {
    color: rgb(65, 46, 28);
    font: 600 28px '';
}

.detailText {
    color: rgb(57, 28, 28);
    padding: 25px 20px;
    border-top: 1px dotted #000;
    margin: 0;
}
</style>
