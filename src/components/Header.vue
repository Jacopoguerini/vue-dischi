<template>
  <header>
      <a href="#">
        <img src="../assets/spotify.png" alt="">
      </a>
  </header>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

header {
    height: 60px;
    display: flex;
    align-items: center;
    background-color: $secondaryBackground;

    img {
        height: 40px;
        margin-left: 10px;
    }
}



</style>