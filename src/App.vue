<script setup>
import Header from './components/Header.vue';
import MdPreview from './components/MdPreview.vue';
</script>


<template>
  <div class="wrap">
    <Header />
    <main class="main"><MdPreview /></main>
  </div>
</template>

<style scoped>
.wrap {
  display: flex;
  flex-direction: column;
}

</style>