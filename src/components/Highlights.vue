<script setup>
import { ref, onMounted } from 'vue';
import { gsap } from 'gsap';
import { watchImg, rightImg } from '../utils';
import VideoCarousel from './VideoCarousel.vue';

const watchImgSrc = ref(watchImg);
const rightImgSrc = ref(rightImg);

onMounted(() => {
    gsap.to('#title', {
        opacity: 1,
        // delay: 1.5,
        y: 0,
    });

    gsap.to('.link', {
        opacity: 1,
        // delay: 2,
        y: 0,
        duration: 1,
        stagger: 0.5,
    });
});

</script>

<template>

    <section id="highlights" class="w-screen overflow-hidden h-full common-padding bg-zinc">
        
        <div class="screen-max-width">
            <div class="mb-12 w-full md:flex items-end justify-between"> 
                <h1 id="title" class="section-heading">Get the highlights.</h1>
                <div class="flex flex-wrap items-end gap-5">
                    <p class="link">Watch the film
                        <img class="ml-2" :src="watchImgSrc" alt="watch">
                    </p>
                    <p class="link">Watch the event
                        <img class="ml-2" :src="rightImgSrc" alt="right">
                    </p>
                </div>
            </div>
            <VideoCarousel>

            </VideoCarousel>
        </div>

    </section>

</template>

<style scoped>

</style>