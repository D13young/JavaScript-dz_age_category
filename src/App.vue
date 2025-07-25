<template>
  <div class="app-container">
    <AgeCategory />
  </div>
</template>

<script setup>
import AgeCategory from './components/AgeCategory.vue'
</script>

<style>
body {
  font-family: 'Arial', sans-serif;
  background-color: #393838;
  margin: 0;
  padding: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}

.app-container {
  width: 100%;
  max-width: 500px;
  margin-left: auto;
  margin-right: auto;
}
</style>