<template>
    
    <div class="hero">
        <JumbotronComponent />
    </div>
    <SliderComponent />
    <div class="d-flex">
        <div class="background_img-right"></div>
        <div class="container movies">
        <strong class="fs-3 m-4 text-white text-center">
        Prossimamente al cinema
        </strong>
            <div class="row d-flex flex-wrap justify-content-between m-auto">
                <div class="col-11 col-sm-6 col-md-5 col-lg-3" v-for="movie in movies" :key="movie.id">
                    <div class="movie-card">
                        <CardComponent :title="movie.title" :description="movie.description" :duration="movie.duration"
                            :image="movie.image" />
                    </div>
                </div>
            </div>
        </div>
        <div class="background_img-left"></div>
    </div>
</template>


<script>
import axios from 'axios';
import { store } from '../store';
import CardComponent from '../components/CardComponent.vue';
import JumbotronComponent from '../components/JumbotronComponent.vue';
import SliderComponent from '../components/SliderComponent.vue';

export default {
    name: 'MovieList',
    components: {
        CardComponent,
        JumbotronComponent,
        SliderComponent
    },

    data() {
        return {
            params: null,
            store,
            movies: [],
            movieList: [
                {
                    title: 'Inception',
                    image: 'https://example.com/images/inception.jpg', 
                }// Sostituisci con l'URL corretto
            ],
           
        }
    },

    methods: {
        getAllMovies() {
            axios.get(this.store.apiBaseUrl + '/movies', { params: this.params }).then((res) => {
                //console.log(res.data);
                this.movies = res.data.results;
                //se paginazione
                //this.posts = res.data.results.data;

            });
        },
    },
    created() {
        this.getAllMovies();

    },
    computed: {

    }

}
</script>

<style>


</style>
