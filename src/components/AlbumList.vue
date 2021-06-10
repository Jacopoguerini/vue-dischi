<template>
    <section class="container">

        <GenreSelection @genreSelected="onGenreSelected"/>

        <div class="albums row" v-if="!loading">
            <div class="column" v-for="(album, index) in albumsGenreFiltered" :key="index">
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
            selectedGenre: ""
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
    },
    methods: {
        onGenreSelected(event) {
            this.selectedGenre = event;
            console.log("Hai selezionato il genere: " + this.selectedGenre);
        }
    },
    computed: {
        albumsGenreFiltered() {
            if (this.selectedGenre == "All") {
                return this.albums;
            }
            const newArray = this.albums.filter(
                (element) => {
                    return element.genre.includes(this.selectedGenre);
                }
            );
            return newArray;
        }
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