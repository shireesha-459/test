<template>
<div>
    <h4 style="text-align:center;">Photo gallery</h4>
    <!-- <button @click="prev()">Previous</button> -->
     <button @click="next()">Next</button>
      <div class="gallery">
        
        <div class="gallery-panel"
            v-for="photo in photos"
            :key="photo.id">
          <router-link :to="`/photo/${photo.id}`">
            <img :src="thumbUrl(photo.filename)" class="zoom">
          </router-link>
        </div>
      </div>
  </div>
</template>

<script>
import photos from '@/photos.json';

export default {
  name: 'Gallery',
  data() {
    return {
      photos,
    };
  },
  methods: {
    thumbUrl(filename) {
      return require(`../assets/images/thumbnails/${filename}`);
    },

    next () {
      this.$router.push('ssr')
    },
  },
};
</script>

<style>
  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(20rem, 1fr));
    grid-gap: 1rem;
    max-width: 80rem;
    margin: 5rem auto;
    padding: 0 5rem;
  }
button{
    background: green;
    color:white;
    padding:10px 20px;
    border:none;
}
  .gallery-panel img {
    width: 100%;
    height: 22vw;
    object-fit: cover;
    border-radius: 0.75rem;
  }
  * {
  box-sizing: border-box;
}

.zoom {
  padding: 10px;
 transition: transform .2s;
  width: 150px;
  height: 150px;

}

.zoom:hover {
  -ms-transform: scale(1.3);
  -webkit-transform: scale(1.3); 
  transform: scale(1.3); 
}
</style>
