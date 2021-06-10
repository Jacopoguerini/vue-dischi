<template>
    <div class="position-absolute top-0 end-0 mt-3 me-3">
        <select v-model="selected">
            <option disabled selected value="">Seleziona un genere </option>
            <option 
                v-for="(album, index) in albums"
                :key="index">
                {{ album.genre }}
            </option>
        </select>
        <!-- <span>{{ selected }}</span> -->
    </div>
</template>

<script>
export default {
    name: "GenreSelection",
    data: function() {
        return {
            selected: ""
        }
    }
}
</script>

<style>

</style>