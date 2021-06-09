<template>
  <section class="container">

    <div class="albums row">
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
                this.albums = response.data.response;
               }
            
            )
            .catch();
    }
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

section {

    .albums {
        justify-content: center;
    }

    .column {
        width: calc((100% / 5) - 3%);
    }

}


</style>