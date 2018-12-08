<template>
  <div class="slide">
    <div class="slide__header">
      <div class="header-title"></div>
      <div class="header-more"></div>
    </div>
    <div class="slide-container"></div>
  </div>
</template>

<script>
  export default {
    name: 'slide',
    props: ['slide']
  }
</script>

<style scoped>
  .slide {
    color: white;
  }
</style>
