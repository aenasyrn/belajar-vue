<template>
  <div class="search-bar">
    <input
      type="text"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
      placeholder="Search events by title or location ... "
      class="search-input"
    />
  </div>
</template>

<script setup>
defineProps({
  modelValue: {
    type: String,
    default: '',
  },
})
defineEmits(['update:modelValue'])
</script>

<style scoped>
.search-bar {
  width: 100%;
  max-width: 500px;
  margin-bottom: 0.75rem;
}

.search-input {
  display: block;
  width: 100%;
  box-sizing: border-box;
  min-height: 48px;
  padding: 0.75rem 1rem;

  background-color: #ffffff;
  color: #1c1948;

  border: 1px solid #dedfe7;
  border-radius: 10px;

  font-size: 1rem;
  line-height: 1.4;

  outline: none;
  box-shadow: none;

  transition:
    border-color 0.2s ease,
    box-shadow 0.2s ease;
}

.search-input::placeholder {
  color: #85859a;
  opacity: 1;
}

.search-input:hover {
  border-color: #b8b8ca;
}

.search-input:focus {
  border-color: #6644ff;
  box-shadow: 0 0 0 3px rgba(102, 68, 255, 0.1);
}

@media (max-width: 768px) {
  .search-bar {
    max-width: 100%;
  }
}
</style>
