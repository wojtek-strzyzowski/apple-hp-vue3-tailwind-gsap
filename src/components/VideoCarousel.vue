<script setup>
import { ref, reactive, onMounted } from 'vue';
import { hightlightsSlides } from '../constants';

const slides = ref(hightlightsSlides);

const video = reactive({
  isEnd: false,
  startPlay: false,
  videoId: 0,
  isLastVideo: false,
  isPlaying: false,
});

const loadData = reactive({
  isLoaded: false,
  isPlaying: false,
  isEnd: false,
  isLastVideo: false,
  videoId: 0,
});

const videoRefs = ref([]); // Initialisiere als leeres Array

onMounted(() => {
  if (loadData.isLoaded && videoRefs.value.length > 3) {
    if (!video.isPlaying) {
      videoRefs.value[video.videoId].pause();
    } else {
      video.startPlay && videoRefs.value[video.videoId].play();
    }
  }
});
</script>

<template>
  <div class="flex items-center space-x-4">
    <div v-for="(slide, index) in slides" :key="slide.id" class="card-container">
      <div class="video-carousel_container">
        <div class="w-full h-full flex-center rounded-3xl overflow-hidden bg-black">
          <video
            :src="slide.video"
            type="video/mp4"
            autoplay
            muted
            playsinline
            :ref="el => {
              if (el) {
                // Stelle sicher, dass videoRefs.value ein Array ist und initialisiere es bei Bedarf
                if (!Array.isArray(videoRefs.value)) {
                  videoRefs.value = [];
                }
                videoRefs.value[index] = el;
              }
            }"
          ></video>
        </div>
        <div class="absolute top-12 left-[5%] z-10">
          <p v-for="(text, i) in slide.textLists" :key="i">
            {{ text }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>


<style scoped>

</style>