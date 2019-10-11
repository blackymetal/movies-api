<template>
  <div class="container">
    <b-card-group deck>
      <b-row>
          <b-col cols="4" v-for="movie in orderForPoints" :key="movie.id">
            <b-card
                :title="movie.title"
                :img-src="`https://image.tmdb.org/t/p/original${movie.backdrop_path}`"
                img-alt="Image"
                img-top
            >
            <puntaje :points="movie.vote_average">
            </puntaje>
            <b-card-text>
                {{ movie.overview }}
            </b-card-text>
                <b-button to="/detail">View Detail</b-button>
            </b-card>
            </b-col>
        </b-row>
    </b-card-group>
  </div>
</template>

<script>
import Logo from "~/components/Logo.vue";
import puntaje from "~/components/puntaje.vue";

export default {
    layout: 'layouts/default',
    components: {
        Logo,
        puntaje
    },
    data() {
        return {
            movies: []
        }
    },
    computed: {
        orderForPoints() {
            return this.movies.sort((a, b) => b.vote_average - a.vote_average )
        }
    },
    async created() {
        //?api_key=86b9417726f5eb3035a288c27beb22f5
        let movies = await this.$axios.get('https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=86b9417726f5eb3035a288c27beb22f5');
        this.movies = movies.data.results;

        console.log(this.movies);
    }
};
</script>

<style>

</style>
