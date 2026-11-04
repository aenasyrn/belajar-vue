<template>
  <div class="category-filter">
    <button
      v-for="cat in categories"
      :key="cat"
      :class="['filter-btn', { active: modelValue === cat }]"
      @click="$emit('update:modelValue', cat)"
    >
      {{ cat }}
    </button>
  </div>
</template>

<script setup>
defineProps({
  categories: {
    type: Array,
    required: true,
  },
  modelValue: {
    type: String,
    default: 'All',
  },
})
defineEmits(['update:modelValue'])
</script>

<style scoped>
.category-filter {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.4rem;
  margin-bottom: 1.5rem;
}

.filter-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;

  padding: 0.35rem 0.8rem;
  min-height: 29px;

  background: #ffffff;
  border: 1px solid #dedfe7;
  border-radius: 999px;

  color: #55556b;
  font-size: 0.75rem;
  font-weight: 500;
  line-height: 1.2;

  cursor: pointer;
  white-space: nowrap;

  transition:
    background-color 0.2s ease,
    border-color 0.2s ease,
    color 0.2s ease;
}

.filter-btn:hover {
  background: #f5f2ff;
  border-color: #6644ff;
  color: #6644ff;
}

.filter-btn.active {
  background: #6644ff;
  border-color: #6644ff;
  color: #ffffff;
}

.filter-btn:focus-visible {
  outline: 2px solid #6644ff;
  outline-offset: 3px;
}
</style>
