<template>
    <div class="slider">
        <button class="nav-button prev" @click="scrollPrev">&#10094;</button>
        <div class="slider-container" ref="sliderContainer">
            <img src="https://backend.ucicinemas.tools/storage/adv-management/carousel//w4dtaC0No5z4Rs12Acjw5nWVMAMpwZrRA5yjD42J.jpg"
                alt="Bad Boys">
            <img src="https://backend.ucicinemas.tools/storage/adv-management/carousel//7xHCOHEoDB5YeygWJnsqYJ0xduYfK0CbzMwhPNRF.png"
                alt="Deadpool">
            <img src="https://backend.ucicinemas.tools/storage/adv-management/carousel//kKh2fiAXGYWWKNPuPFJx9o6aogSPIh0mvkGAHl06.png"
                alt="Inside Out">
            <img src="https://backend.ucicinemas.tools/storage/adv-management/carousel//43If9g6lNt89jUJQippV1KSPQm1ff6jDoafsYNSz.png"
                alt="Inside out 2">
            <img src="https://backend.ucicinemas.tools/storage/adv-management/carousel//WoLu5farXMXPB68nyAWTfk9zdw6b8P8uZcAFubkG.png"
                alt="Deadpool Wolverine">
        </div>
        <button class="nav-button next" @click="scrollNext">&#10095;</button>
    </div>
</template>



<script>
import { store } from '../store';

export default {
    name: 'SliderComponent',
    methods: {
        scrollNext() {
            const slider = this.$refs.sliderContainer;
            slider.scrollBy({ left: 300, behavior: 'smooth' }); // Scorri 300px a destra
        },
        scrollPrev() {
            const slider = this.$refs.sliderContainer;
            slider.scrollBy({ left: -300, behavior: 'smooth' }); // Scorri 300px a sinistra
        }
    }
}

</script>

<style lang="scss" scoped>
.slider {
    position: relative;
    width: 100%;
    display: flex;
    align-items: center;
}

.slider-container {
    display: flex;
    overflow-x: scroll;
    scroll-behavior: smooth;
    width: 100%;
    scroll-snap-type: x mandatory;
}

.slider-container::-webkit-scrollbar {
    display: none;
    /* Nascondi la scrollbar */
}


.nav-button {
    background-color: rgba(0, 0, 0, 0.5);
    border: none;
    color: white;
    font-size: 2em;
    cursor: pointer;
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    z-index: 1;
    padding: 10px;
    border-radius: 50%;
}

.nav-button.prev {
    left: 10px;
}

.nav-button.next {
    right: 10px;
}

.nav-button:hover {
    background-color: rgba(0, 0, 0, 0.8);
}

.slider img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}
</style>
