<script setup>

</script>

<template>
<div id="detailList">
    <details>
        <summary>下拉清單1</summary>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Iusto sed assumenda voluptate debitis perferendis harum eligendi commodi quo aspernatur accusamus! Sunt suscipit explicabo voluptatibus quaerat eos quod consequuntur ipsam minima!</p>
    </details>
    <details>
        <summary>下拉清單2</summary>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Iusto sed assumenda voluptate debitis perferendis harum eligendi commodi quo aspernatur accusamus! Sunt suscipit explicabo voluptatibus quaerat eos quod consequuntur ipsam minima!</p>
    </details>
    <details>
        <summary>下拉清單3</summary>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Iusto sed assumenda voluptate debitis perferendis harum eligendi commodi quo aspernatur accusamus! Sunt suscipit explicabo voluptatibus quaerat eos quod consequuntur ipsam minima!</p>
    </details>
</div>

</template>

<style scoped>
#detailList{
    user-select: none;
    text-align: start;
    display: flex;
    flex-direction: column;
}
#detailList details{
    padding: 20px 0;
}
</style>
