<script setup>
import { ref, computed } from 'vue'
import { useRouter } from 'vue-router'
import EventCard from '@/components/event/EventCard.vue'
import SearchBar from '@/components/event/SearchBar.vue'
import CategoryFilter from '@/components/event/CategoryFilter.vue'

const router = useRouter()
const events = [
  {
    id: 1,
    title: 'Vue.js Mastery Workshop',
    date: 'Oct 12, 2026',
    loc: '📍Tech Hub, Jakarta',
    cat: 'Workshop',
    desc: 'Learn advanced Vue 3 concepts, Composition API, and state management to build high-performance web applications interactively.',
  },
  {
    id: 2,
    title: 'National Tech Meetup',
    date: 'Oct 15, 2026',
    loc: '📍Main Auditorium, City Center',
    cat: 'Meetup',
    desc: 'A gathering of hundreds of developers and tech enthusiasts to share the latest trends and expand professional networks.',
  },
  {
    id: 3,
    title: 'Startup Pitch Competition',
    date: 'Nov 02, 2026',
    loc: '📍Innovation Center',
    cat: 'Competition',
    desc: 'Watch the best local startup founders pitch their innovative ideas live.',
  },
  {
    id: 4,
    title: 'UI/UX Design Sprint',
    date: 'Nov 10, 2026',
    loc: '📍Creative Studio',
    cat: 'Workshop',
    desc: 'A hands-on session on designing user interfaces by implementing layout systems and visual hierarchy principles.',
  },
  {
    id: 5,
    title: 'Digital Marketing Seminar',
    date: 'Nov 20, 2026',
    loc: '📍Grand Hotel Hall',
    cat: 'Seminar',
    desc: 'An in-depth seminar dissecting modern digital marketing strategies, from SEO optimization to user conversion tactics.',
  },
  {
    id: 6,
    title: 'Community Leaders Summit',
    date: 'Dec 05, 2026',
    loc: '📍Gatherly HQ',
    cat: 'Conference',
    desc: 'An exclusive year-end conference for community leaders to formulate sustainable ecosystem development strategies.',
  },
]

const searchQuery = ref('')
const selectedCategory = ref('All')
const categories = ['All', 'Workshop', 'Meetup', 'Competition', 'Seminar', 'Conference']

const filteredEvents = computed(() => {
  return events.filter((event) => {
    const matchSearch =
      event.title.toLowerCase().includes(searchQuery.value.toLowerCase()) ||
      event.loc.toLowerCase().includes(searchQuery.value.toLowerCase())
    const matchCat = selectedCategory.value === 'All' || event.cat === selectedCategory.value
    return matchSearch && matchCat
  })
})

const handleViewDetail = (id) => {
  router.push(`/browse/events/${id}`)
}
</script>

<template>
  <div class="event-list-page">
    <div class="header-section">
      <h2 class="section-title">Upcoming Events</h2>
      <p class="section-desc">
        Discover workshops, seminars, tech meetups, and competitions near you .
      </p>
    </div>

    <div class="filters-section">
      <SearchBar v-model="searchQuery" />
      <CategoryFilter :categories="categories" v-model="selectedCategory" />
    </div>

    <div class="event-grid">
      <EventCard
        v-for="event in filteredEvents"
        :key="event.id"
        :event="event"
        @view-detail="handleViewDetail"
      />
    </div>

    <div v-if="filteredEvents.length === 0" class="empty-state">
      <p>No events found matching your criteria .</p>
    </div>
  </div>
</template>

<style scoped>
.event-list-page {
  width: 100%;
  min-width: 0;
  color: #1c1948;
}

.header-section {
  margin-bottom: 1.5rem;
}

.section-title {
  color: #1c1948;
  font-size: 2rem;
  font-weight: 700;
  line-height: 1.3;
  margin-bottom: 0.5rem;
}

.section-desc {
  color: #666780;
  font-size: 1rem;
  line-height: 1.6;
}

.filters-section {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 1rem;
  margin-bottom: 1.5rem;
  width: 100%;
}

.event-grid {
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  gap: 1rem;
  align-items: stretch;
  width: 100%;
}

.empty-state {
  text-align: center;
  padding: 3rem 1rem;
  color: #666780;
  background: #f8f9fc;
  border: 1px solid #e3e5ed;
  border-radius: 12px;
}

@media (max-width: 1100px) {
  .event-grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }
}

@media (max-width: 600px) {
  .section-title {
    font-size: 1.7rem;
  }

  .event-grid {
    grid-template-columns: minmax(0, 1fr);
  }
}
</style>
