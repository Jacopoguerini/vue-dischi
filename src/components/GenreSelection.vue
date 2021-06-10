<template>
    <div class="position-absolute top-0 end-0 mt-3 me-3">
        <select v-model="selection" @change="$emit('genreSelected', selection)">
            <option disabled selected value="">Seleziona un genere</option>
            <option value="All">Tutti i generi</option>
            <option :value="genre" v-for="(genre, index) in genres" :key="index">{{ genre }}</option>
            <!-- <option value="Rock">Rock</option>
            <option value="Pop">Pop</option>
            <option value="Jazz">Jazz</option>
            <option value="Metal">Metal</option> -->
        </select>
        <!-- <span>{{ selection }}</span> -->
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: "GenreSelection",
    data: function() {
        return {
            selection: "",
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
            genres: [],
        }
    },
        created: function() {
    axios
        .get(this.apiUrl)
        .then(
            (response) => {
                this.genres = response.data.response.genre;
            }
        )
        .catch();
    }
}
</script>

<style>

</style>