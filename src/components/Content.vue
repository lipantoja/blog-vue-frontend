<script>
import axios from "axios";
import PhotosIndex from "./PhotosIndex.vue";

export default {
  components: {
    PhotosIndex,
  },
  data: function () {
    return {
      photos: [
        { id: 1, name: "First", url: "https://via.placeholder.com/150", width: 150, height: 150 },
        { id: 2, name: "Second", url: "https://via.placeholder.com/300", width: 300, height: 300 },
      ],
    };
  },
  created: function () {
    this.handleIndexPhotos();
  },
  methods: {
    handleIndexPhotos: function () {
      axios.get("http://localhost:3000/photos.json").then((response) => {
        console.log("photos index", response);
        this.photos = response.data;
      });
    },
  },
};
</script>

<template>
  <main>
    <PhotosIndex v-bind:photos="photos"/>
  </main>
</template>

<style></style>