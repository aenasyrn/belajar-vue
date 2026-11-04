<template>
  <div class="app-card">
    <slot />
  </div>
</template>

<style scoped>
.app-card {
  width: 100%;
  min-width: 0;
  height: 100%;
  background: #ffffff;
  border: 1px solid #dedfe7;
  border-radius: 12px;
  box-shadow: 0 2px 6px rgba(28, 25, 72, 0.05);
  transition:
    transform 0.2s ease,
    box-shadow 0.2s ease;
  overflow: hidden;
}

.app-card:hover {
  transform: translateY(-3px);
  box-shadow: 0 5px 16px rgba(28, 25, 72, 0.1);
}
</style>
