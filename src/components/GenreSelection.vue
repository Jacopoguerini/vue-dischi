<template>
    <div>
        <select v-model="selection" @change="$emit('genreSelected', selection)">
            <option disabled selected value="">Seleziona un genere</option>
            <option value="All">Tutti i generi</option>
            <!-- <option :value="album.genre" v-for="(album, index) in item" :key="index">{{ album.genre }}</option> -->
            <option value="Rock">Rock</option>
            <option value="Pop">Pop</option>
            <option value="Jazz">Jazz</option>
            <option value="Metal">Metal</option>
        </select>
        <!-- <span>{{ selection }}</span> -->
    </div>
</template>

<script>
export default {
    name: "GenreSelection",
    props: [ "item" ],
    data: function() {
        return {
            selection: "",
            uniqueGenres: []
        }
    }
}
</script>

<style>

</style>