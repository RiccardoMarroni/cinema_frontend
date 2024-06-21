<template>
    <div class="movie-card">
        <div class="movie-poster" :style="{ backgroundImage: 'url(' + getImage + ')' }">
            <div class="movie-overlay">
                <div class="movie-info">
                    <h3 class="movie-title">{{ title }}</h3>
                    <p class="movie-description">
                        <strong>Description:</strong>
                        {{ description }}
                    </p>
                    <span class="movie-duration">
                        <strong>Duration:</strong>
                        {{ duration }}</span>
                </div>
            </div>
        </div>
    </div>
</template>


<script>
import { store } from '../store';
export default {
    name: 'CardComponent',
    components: {

    },
    props: ['id', 'title', 'image', 'description', 'duration'],
    data() {
        return {
            store,
            movie: this.item,

        }
    },
    methods: {

    },
    computed: {
        getImage() {
            return this.store.imgBasePath + this.image
        }
    },
    mounted() {

    },
    created() {

    }
}
</script>

<style lang="scss" scoped>
.movie-card {
    position: relative;
    width: 200px;
    height: 300px;
    margin: 20px;
    overflow: hidden;
    transition: transform 0.3s ease;
    cursor: pointer;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}

.movie-card:hover {
    transform: scale(1.05);
}

.movie-poster {
    width: 100%;
    height: 100%;
    background-size: cover;
    background-position: center;
    position: relative;
}

.movie-overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.6);
    opacity: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    color: white;
    text-align: center;
    padding: 20px;
    transition: opacity 0.3s ease;
}

.movie-card:hover .movie-overlay {
    opacity: 1;
}

.movie-info {
    padding: 10px;
}

.movie-title {
    font-size: 1.5em;
    font-weight: bold;
    margin-bottom: 10px;
}

.movie-description {
    font-size: 1em;
    margin-bottom: 10px;
}

.movie-duration {
    font-size: 0.9em;
    color: #ddd;
}
</style>
