<template>
    <div>
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
export default {
    name: "GenreSelection",
    props: [ "genres" ],
    data: function() {
        return {
            selection: "",
        }
    }
}
</script>

<style>

</style>