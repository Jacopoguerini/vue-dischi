<template>
  <section class="albums container">

    <div class="row">
        <div class="column" v-for="(album, index) in albums" :key="index">
            <Album :item="album"/>
        </div>

    </div>

  </section>
</template>

<script> 
import Album from './Album';
import axios from 'axios';

export default {
    name: "AlbumList",
    components: {
        Album
    },
    data: function() {
        return {
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
            albums: []
        }
    },
    created: function() {
        axios
            .get(this.apiUrl)
            .then(
               (response) => {
                this.albums = response.data;
               }
            )
            .catch();
    }
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

section {
    background-color: red;
    height: 500px;

    .column {
        width: calc((100% / 5) - 25px);
    }
}


</style>