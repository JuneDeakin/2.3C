<!-- BirdItem.vue -->
<template>
    <div class="bird-item">
    <h3>
      <router-link :to="'/' + bird.path">{{ bird.name }}</router-link>
    </h3>
    <p>{{ bird.description }}</p>
  </div>
  </template>
  
  <script>
  export default {
    props: {
      bird: {
        type: Object,
        required: true
      }
    }
  };
  </script>
  
  <style scoped>
  .bird-item {
  margin-bottom: 20px;
}
.bird-item h3 {
  margin-bottom: 5px;
}
  </style>
  