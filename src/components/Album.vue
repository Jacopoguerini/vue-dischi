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
        height: 280px;
        padding: 20px 10px;
        background-color: $secondaryBackground;
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;
        margin-bottom: 15px;

        img {
            width: 150px;
            margin-bottom: 15px;
            cursor: pointer;
        }

        h3 {
            font-size: 14px;
            color: $titleColor;
            text-transform: uppercase;
            font-weight: 600;
            padding: 0 15px;
        }

        h5 {
            font-size: 12px;
            color: $secondaryColor;
        }
    }

</style>