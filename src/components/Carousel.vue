<template>
    <h3>Vue Carousel</h3>
    <hr>
    <div id="carouselExampleIndicators" class="carousel slide">
        <ol class="carousel-indicators">
            <li @click="activeIndex = index" v-for="(slide, index) in slides" :key="index"
                :class="index == activeIndex ? 'active' : ''"></li>
        </ol>
        <div class="carousel-inner">
            <div class="carousel-item active">
                <img :src="slides[activeIndex].image" class="d-block w-100" height="500" alt="...">
            </div>
        </div>
        <a @click.prevent="0 == activeIndex ? activeIndex = (slides.length) - 1 : activeIndex--"
            class="carousel-control-prev" href="#" role="button">
            <span class="carousel-control-prev-icon" aria-hidden="true"></span>
            <span class="sr-only">Previous</span>
        </a>
        <a @click.prevent="(slides.length) - 1 == activeIndex ? activeIndex = 0 : activeIndex++" class="carousel-control-next"
            href="#" role="button">
            <span class="carousel-control-next-icon" aria-hidden="true"></span>
            <span class="sr-only">Next</span>
        </a>
    </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue"

const activeIndex = ref(0)

const slides = [
    {
        image: 'https://images.unsplash.com/photo-1689702095123-a20606125fd5?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80',
    },
    {
        image: 'https://images.unsplash.com/photo-1689199784023-9aaad19418eb?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80',
    },
    {
        image: 'https://images.unsplash.com/photo-1653699723691-ba91de1e4de9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1471&q=80',
    },
    {
        image: 'https://images.unsplash.com/photo-1688490475768-8cf222afdec3?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1632&q=80',
    },
    {
        image: 'https://images.unsplash.com/photo-1675966356873-06f6eedffeb6?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1631&q=80',
    },
]


const slide = function () {
    setInterval(() => {
        if (activeIndex.value == slides.length - 1) {
            activeIndex.value = 0
        }
        else {
            activeIndex.value++
        }
    }, 3000)
}

onMounted(() => {
    slide()
})

</script>