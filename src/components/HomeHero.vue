<template>
    <v-container fluid fill-height class="home-hero" style="max-height: 100vh;">
        <v-layout justify-center align-center column pa-5>
            <div class="display-3 font-weight-black white--text text-xs-center">Culture Map</div>
            <div class="display-2 font-weight-black white--text text-xs-center mb-3">Une envie de sortie ?</div>
            <div class="display-1 font-weight-bold white--text text-xs-center">"Théâtre, Musée, Patrimoine, la culture à proximité d'un seul clic"</div>
            <v-btn fab class="mt-5 indigo darken-4">
            <v-icon large color="white">Go</v-icon>
            </v-btn>
        </v-layout>
    </v-container>
</template>

<script>
export default {
    name: 'Home'
};
</script>

<style scoped>
.home-hero {
    background: url('http://source.unsplash.com/EjXX-vhMdLI');
    background-size: cover;
    
    width: 100%;
    height: 100%;
}
</style>