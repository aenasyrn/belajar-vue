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
  display: flex;
  flex-direction: column;
  background-color: var(--bg-light, #fdfdfd);
}

.main-content {
  flex: 1;
  padding: 2rem 2.5rem;
  max-width: 1440px;
  margin: 0 auto;
  width: 100%;
  box-sizing: border-box;
}

@media (max-width: 768px) {
  .main-content {
    padding: 1rem;
  }
}
</style>
