<template>
    <section class="container">

        <GenreSelection />

        <div class="albums row" v-if="!loading">
            <div class="column" v-for="(album, index) in albums" :key="index">
                <Album :item="album"/>
            </div>
        </div>
        <Loader v-else />

    </section>
</template>

<script> 
import Album from './Album';
import axios from 'axios';
import Loader from './Loader';
import GenreSelection from './GenreSelection';

export default {
    name: "AlbumList",
    components: {
        Album,
        Loader,
        GenreSelection
    },
    data: function() {
        return {
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
            albums: [],
            loading: true,
        }
    },
    created: function() {
        axios
            .get(this.apiUrl)
            .then(
                (response) => {
                    this.albums = response.data.response;
                    // setTimeout( () => {
                        this.loading = false;
                    // }, 3800);
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

    .filter {
        text-align: right;
    }

}


</style>