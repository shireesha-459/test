<template>
<div>
    <h4 style="text-align:center;">Photo gallery</h4>
     <button @click="prev()">Previous</button>
     
      <div class="gallery">
        
        <div class="gallery-panel"
            v-for="photoo in photoos"
            :key="photoo.id">
          
            <img :src="thumbUrl(photoo.filename)" class="zoom">
        
        </div>
      </div>
  </div>
</template>

<script>

import photoos from '@/photoos.json';
export default {
  name: 'ssr',
  data() {
    return {
      photoos,
    };
  },
   methods: {
    thumbUrl(filename) {
      return require(`../assets/images/thumbnails/${filename}`);
    },

    prev () {
      this.$router.push('photo/id')
    },
  },
};
</script>
<style scoped>
button{
    background: green;
    color:white;
    padding:10px 20px;
    border:none;
}


</style>

