<template>
  <div ref="videoContainer" class="video-container">
    <video ref="videoPlayer" autoplay muted :src="videoSrc" class="fullscreen-video"></video>
  </div>
</template>

<script setup>
import { ref, watchEffect } from 'vue';
import { useIdle } from '@vueuse/core';

const videoSrc = 'http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/ForBiggerBlazes.mp4';
const videoContainer = ref(null);
const videoPlayer = ref(null);

// Detect idle state
const { isIdle } = useIdle(30000); // 30 seconds

// Open video fullscreen after 30 seconds of inactivity
watchEffect(() => {
  console.log(isIdle);
  if (isIdle) {
    openFullscreen();
    playVideo();
  }
});

// Open video in fullscreen
function openFullscreen() {
  if (videoContainer.value.requestFullscreen) {
    videoContainer.value.requestFullscreen();
  }
}

// Play video
function playVideo() {
  videoPlayer.value.play();
}
</script>

<style scoped>
.video-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: black;
  z-index: 9999;
}

.fullscreen-video {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>
