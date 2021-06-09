<template>
    <div class="album">
        <img class="img-fluid" :src="item.poster" :alt="item.title">
        <h3>{{ item.title }}</h3>
        <h5>{{ item.author }}<br>
            {{ item.year }}</h5>
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
        padding: 10px;
        background-color: $secondaryBackground;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        text-align: center;

        img {
            width: 100px;
        }

        h3 {
            font-size: 16px;
            color: $titleColor;
            text-transform: uppercase;
            font-weight: 600;
        }

        h5 {
            font-size: 12px;
            color: $secondaryColor;
        }
    }

</style>