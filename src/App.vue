<script setup>
import SearchWrapper from './components/SearchWrapper.vue';
import '@/assets/css/vendor/minireset.min.css';
import '@/assets/css/common.css';
</script>

<template>
  <main>
    <SearchWrapper />
  </main>
</template>

<style>
main {
  display: flex;
  min-height: 100vh;
  padding: 0 10px;
  background-image: linear-gradient(130deg, #4545c0 0%, #5caaeb 100%);
}
</style>
