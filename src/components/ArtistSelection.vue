<template>
    <div>
        <select v-model="selection" @change="$emit('artistSelected', selection)">
            <option disabled selected value="">Seleziona un artista</option>
            <option value="All">Tutti gli artisti</option>
            <option :value="album.author" v-for="(album, index) in item" :key="index">{{ album.author }}</option>
        </select>
        <!-- <span>{{ selection }}</span> -->
    </div>
</template>

<script>
export default {
    name: "ArtistSelection",
    props: [ "item" ],
    data: function() {
        return {
            selection: ""
        }
    }
}
</script>

<style>

</style>