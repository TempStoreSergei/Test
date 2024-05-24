<template>
    <vue-pdf-app page-scale='auto' :config="config" pdf="present.pdf" style="height: 100vh; width: 100vw;"></vue-pdf-app>
  </template>
  
  <script setup>
  import VuePdfApp from "vue3-pdf-app";
  // import this to use default icons for buttons
  import "vue3-pdf-app/dist/icons/main.css";

  const config = {
    toolbar: false,
  }

  </script>

<style>
.page {
    border: none !important;
    margin: 0 !important;
    width: 100% !important;
}
</style>