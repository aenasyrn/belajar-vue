<template>
  <AppCard class="event-card-wrapper">
    <div class="event-body">
      <div class="event-meta">
        <span class="event-date">{{ event.date }}</span>
        <span class="event-category">{{ event.cat }}</span>
      </div>

      <h3 class="event-title">{{ event.title }}</h3>
      <p class="event-loc">{{ event.loc }}</p>
      <p class="event-desc">{{ event.desc }}</p>

      <div class="card-footer">
        <button class="btn-link" @click="$emit('view-detail', event.id)">
          View Event Details &rarr;
        </button>
      </div>
    </div>
  </AppCard>
</template>

<script setup>
import AppCard from '@/components/ui/AppCard.vue'

defineProps({
  event: {
    type: Object,
    required: true,
  },
})
defineEmits(['view-detail'])
</script>

<style scoped>
.event-card-wrapper {
  display: flex;
  flex-direction: column;
  height: 100%;
  min-width: 0;
  background: #ffffff;
  border: 1px solid #dedfe7;
  border-radius: 12px;
  box-shadow: 0 2px 6px rgba(28, 25, 72, 0.05);
  overflow: hidden;
  transition:
    transform 0.2s ease,
    box-shadow 0.2s ease;
}

.event-card-wrapper:hover {
  transform: translateY(-3px);
  box-shadow: 0 5px 16px rgba(28, 25, 72, 0.1);
}

.event-body {
  padding: 1.25rem;
  display: flex;
  flex-direction: column;
  flex: 1;
  min-width: 0;
}

.event-meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 0.5rem;
  margin-bottom: 1.25rem;
}

.event-date {
  display: inline-block;
  background: #f0ebff;
  color: #6644ff;
  padding: 0.2rem 0.45rem;
  border-radius: 4px;
  font-weight: 600;
  font-size: 0.75rem;
  white-space: nowrap;
}

.event-category {
  color: #55556b;
  font-size: 0.7rem;
  font-weight: 600;
  text-transform: uppercase;
  text-align: right;
}

.event-title {
  color: #1c1948;
  margin: 0 0 0.75rem;
  font-size: 1.1rem;
  font-weight: 700;
  line-height: 1.4;
  overflow-wrap: anywhere;
}

.event-loc {
  color: #666780;
  font-size: 0.85rem;
  line-height: 1.5;
  margin: 0 0 1rem;
}

.event-desc {
  color: #666780;
  line-height: 1.55;
  font-size: 0.85rem;
  margin: 0 0 1.25rem;
  flex-grow: 1;
}

.card-footer {
  border-top: 1px solid #e0e1e8;
  padding-top: 0.85rem;
  margin-top: auto;
}

.btn-link {
  display: inline-block;
  background: transparent;
  border: none;
  cursor: pointer;
  color: #1c1948;
  font-weight: 600;
  text-decoration: none;
  font-size: 0.85rem;
  padding: 0;
  text-align: left;
}

.btn-link:hover {
  color: #6644ff;
}

.btn-link:focus-visible {
  outline: 2px solid #6644ff;
  outline-offset: 4px;
  border-radius: 2px;
}
</style>
