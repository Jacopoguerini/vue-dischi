<template>
    <div class="album">
        <img class="img-fluid" :src="item.poster" :alt="item.title">
    </div>
</template>

<script>
export default {
    name: "Album",
    props: [ "item" ]
}
</script>

<style lang="scss" scoped>
    @import '../style/variables.scss';

    .album {
        height: 100px;
        background-color: chartreuse;
    }

</style>