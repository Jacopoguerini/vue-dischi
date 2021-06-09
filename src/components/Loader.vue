<template>
    <div class="loader">
        <img src="../assets/spotify2.gif" alt="">
    </div>
</template>

<script>
export default {
    name: "Loader"
}
</script>

<style lang="scss" scoped>
    @import '../style/variables.scss';
    
    .loader {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: #f9f9f9;
    }
</style>