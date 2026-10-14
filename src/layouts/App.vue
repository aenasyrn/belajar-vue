<script setup lang="ts">
import Navbar from '@/components/app/Navbar.vue'
import Breadcrumb from '@/components/app/Breadcrumb.vue'
</script>

<template>
  <div class="app-layout">
    <Navbar />
    <main class="main-content">
      <Breadcrumb />
      <router-view />
    </main>
  </div>
</template>

<style scoped>
.app-layout {
  min-height: 100vh;
  width: 100%;
  display: flex;
  flex-direction: column;
  box-sizing: border-box;
}

.main-content {
  flex: 1;
  width: 100%;
  max-width: none;
  margin: 0;
  padding: 2rem;
  box-sizing: border-box;
}
</style>
