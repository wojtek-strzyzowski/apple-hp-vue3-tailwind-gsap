<script setup>
import { ref, onMounted } from 'vue';
import { gsap } from 'gsap';
import { heroVideo, smallHeroVideo } from '../utils';

const videoSRC = ref(heroVideo);

const updateVideoSRC = () => {
  if (window.innerWidth < 768) {
    videoSRC.value = smallHeroVideo;
  } else {
    videoSRC.value = heroVideo;
  }
};

onMounted(() => {
  gsap.to('#hero', {
    opacity: 1,
    delay: 1.5,
  });

  updateVideoSRC();
  window.addEventListener('resize', updateVideoSRC);
});
</script>

<template>
    <section class="w-full nav-height bg-black relative">
        <div class="h-5/6 w-full flex-center flex-col">
            <p id="hero" class="hero-title">iPhone 15 Pro</p>
            <div class="md:w-10/12 w-9/12">
                <video class="pointer-events-none" :src="videoSRC" type="video/mp4" autoplay muted playsinline></video>
            </div>
        
        </div>
    </section>

</template>

<style scoped>

</style>