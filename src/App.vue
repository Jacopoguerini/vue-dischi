<template>
  <div id="app">
    <Header />

    <main>


    </main>


  </div>
</template>

<script>
import Header from './components/Header';

export default {
  name: 'App',
  components: {
    Header
  }
}
</script>

<style lang="scss">
@import './style/general.scss';
@import './style/variables.scss';

#app {
  height: 100vh;
}

main {
  height: calc(100vh - 60px);
  background-color: $mainBackground;
}

</style>
