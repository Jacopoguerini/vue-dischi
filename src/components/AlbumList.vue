<template>
    <section class="container">

        <div class="filters position-absolute top-0 end-0 me-3 mt-1">
            <GenreSelection
            @genreSelected="onGenreSelected"
            :genres="allGenres"
            />

            <ArtistSelection
            @artistSelected="onArtistSelected"
            :item="albums"
            />
        </div>

        <div class="albums row" v-if="!loading">
            <div class="column" v-for="(album, index) in albumsFiltered" :key="index">
                <Album :item="album"/>
            </div>
        </div>
        <Loader v-else />

    </section>
</template>s

<script> 
import Album from './Album';
import axios from 'axios';
import Loader from './Loader';
import GenreSelection from './GenreSelection';
import ArtistSelection from './ArtistSelection';

export default {
    name: "AlbumList",
    components: {
        Album,
        Loader,
        GenreSelection,
        ArtistSelection
    },
    data: function() {
        return {
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
            albums: [],
            allGenres: [],
            artists: [],
            loading: true,
            selectedGenre: "",
            selectedArtist: ""
        }
    },
    created: function() {
    axios
        .get(this.apiUrl)
        .then(
            (response) => {
                this.albums = response.data.response;

                this.albums.forEach(
                    (element) => {
                        if (!this.allGenres.includes(element.genre)) {
                            this.allGenres.push(element.genre);
                        }
                        
                        if (!this.artists.includes(element.genre)) {
                            this.artists.push(element.author);
                        } 
                    }
                );
                // console.log(this.allGenres);
                // console.log(this.artists);

                // setTimeout( () => {
                this.loading = false;
                // }, 3500);
            }
        )
        .catch();
    },
    methods: {
        onGenreSelected(event) {
            this.selectedGenre = event;
            this.selectedArtist = "All";
        },
        onArtistSelected(event) {
            this.selectedArtist = event;
            this.selectedGenre = "All";
        }
    },
    computed: {
        albumsFiltered: function() {
            if (this.selectedGenre == "All" && this.selectedArtist == "All") {
                return this.albums;
            } else if (this.selectedArtist != "All") {
                return this.albums.filter(
                    (element) => {
                    return element.author.includes(this.selectedArtist);
                });
            }

            return this.albums.filter(
                (element) => {
                    return element.genre.includes(this.selectedGenre);
                }
            );
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