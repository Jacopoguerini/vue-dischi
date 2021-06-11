<template>
  <div id="app" class="position-relative">
    <Header />

    <main>
      <AlbumList />

    </main>


  </div>
</template>

<script>
import Header from './components/Header';
import AlbumList from './components/AlbumList';

export default {
  name: 'App',
  components: {
    Header,
    AlbumList,
  },
  data: function() {
    return {
    }
  },
  methods: {
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
  display: flex;
  justify-content: center;
  align-items: center;
}

</style>
