<script setup>
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header class="container mx-auto mb-6">
    <img alt="Vue logo" class="logo mb-4" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper mx-auto">
      <HelloWorld msg="Welcome to vue api project" />
    </div>
  </header>


<div  class=" container mx-auto columns-4 gap-8">
  <div v-for="photo in Photos" class=" w-full border px-4  mt-10">
    <div class="border border-gray-200 mb-4 h-auto">
      <li class="list-none">id = {{ photo.id }}</li>
      <li class="list-none"> albumId = {{ photo.albumId }}</li>
      <h1 class="">title = {{ photo.title }}</h1>
      <img class="aspect-video w-full" :src="photo.thumbnailUrl" :alt="photo.title">
      <p> {{ photo.url }}</p>

    </div>
  </div>
</div>




</template>



<script>
  export default {
    data() {
      return {
        Photos: []
      }
    },
    methods: {
      async getData() {
        const res = await fetch("https://jsonplaceholder.typicode.com/photos");
        const finalRes = await res.json();
        this.Photos = finalRes;
      }
    },
    mounted() {
      this.getData()
    }
  }
</script>

<style scopped>
 

</style>

