<script setup>
import AppButton from '@/components/ui/AppButton.vue'
import AppCard from '@/components/ui/AppCard.vue'
</script>

<template>
  <div class="event-detail-page">
    <!-- Tombol kembali -->
    <button type="button" class="btn-back" @click="$router.push('/browse/events')">
      &larr; Back to Events
    </button>

    <!-- Header event -->
    <header class="detail-header">
      <span class="event-tag">Workshop &amp; Training</span>

      <h1>Vue.js Mastery Workshop {{ $route.params.id }}</h1>

      <div class="meta-info">
        <span class="meta-item">📅 October 12, 2026</span>
        <span class="meta-item">📍 Tech Hub, Jakarta Pusat</span>
        <span class="meta-item">🎟️ Quota: 150 Attendees</span>
      </div>
    </header>

    <!-- Konten utama -->
    <div class="detail-content">
      <section class="main-desc">
        <h2>About This Event</h2>

        <p>
          Welcome to the biggest web interface development training event of the year! Gatherly is
          collaborating with the local developer community to host a comprehensive workshop designed
          specifically to bring together professionals, enthusiasts, and students.
        </p>

        <p>
          In this session, we will discuss current industry challenges, explore the implementation
          of Single Page Applications (SPA), and practice hands-on layout system design with a focus
          on visual hierarchy.
        </p>

        <h2>Agenda</h2>

        <ul class="agenda-list">
          <li>
            <strong>09:00 AM</strong>
            <span>Registration &amp; Welcome Coffee</span>
          </li>
          <li>
            <strong>10:00 AM</strong>
            <span>Opening Keynote Speech</span>
          </li>
          <li>
            <strong>11:30 AM</strong>
            <span>Networking Session</span>
          </li>
          <li>
            <strong>01:00 PM</strong>
            <span>Closing Remarks</span>
          </li>
        </ul>
      </section>

      <!-- Kartu registrasi -->
      <aside class="sidebar">
        <AppCard class="ticket-card">
          <h3>Attendee Registration</h3>

          <p class="price">Free</p>

          <p class="ticket-desc">Secure your seat now before the quota is full.</p>

          <AppButton variant="primary" class="btn-register"> Register Now </AppButton>

          <p class="spots">Only 12 spots left!</p>
        </AppCard>
      </aside>
    </div>
  </div>
</template>

<style scoped>
/* ===== HALAMAN UTAMA ===== */
.event-detail-page {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding-bottom: 3rem;
  color: var(--text-main, #1c1948);
}

/* ===== TOMBOL KEMBALI ===== */
.btn-back {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
  padding: 0.5rem 0;

  background: transparent;
  border: none;
  color: var(--text-muted, #666780);

  font-size: 0.95rem;
  font-weight: 600;
  cursor: pointer;

  transition: color 0.2s ease;
}

.btn-back:hover {
  color: var(--primary, #6644ff);
}

/* ===== HEADER EVENT ===== */
.detail-header {
  margin-bottom: 2rem;
  padding: 2.5rem;

  background: var(--bg-light, #f8f7ff);
  border: 1px solid var(--border-color, #e2e2eb);
  border-radius: 16px;
}

.event-tag {
  display: inline-block;
  margin-bottom: 1rem;
  padding: 0.4rem 0.85rem;

  background: rgba(102, 68, 255, 0.1);
  border-radius: 999px;
  color: var(--primary, #6644ff);

  font-size: 0.85rem;
  font-weight: 600;
}

.detail-header h1 {
  margin: 0 0 1.25rem;
  color: var(--text-main, #1c1948);

  font-size: clamp(1.8rem, 4vw, 2.7rem);
  font-weight: 800;
  line-height: 1.25;
  overflow-wrap: anywhere;
}

.meta-info {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem 1.5rem;
}

.meta-item {
  color: var(--text-muted, #666780);
  font-size: 0.9rem;
  font-weight: 500;
}

/* ===== LAYOUT DUA KOLOM ===== */
.detail-content {
  display: grid;
  grid-template-columns: minmax(0, 1fr) 320px;
  align-items: start;
  gap: 2rem;
}

.main-desc,
.sidebar {
  min-width: 0;
}

/* ===== DESKRIPSI EVENT ===== */
.main-desc {
  padding: 0.25rem 0;
}

.main-desc h2 {
  margin: 0 0 1rem;
  padding-left: 0.85rem;

  border-left: 4px solid var(--primary, #6644ff);
  color: var(--text-main, #1c1948);

  font-size: 1.5rem;
  font-weight: 700;
  line-height: 1.4;
}

.main-desc h2:not(:first-child) {
  margin-top: 2rem;
}

.main-desc p {
  margin: 0 0 1.25rem;
  color: var(--text-muted, #666780);

  font-size: 0.98rem;
  line-height: 1.8;
}

/* ===== AGENDA ===== */
.agenda-list {
  margin: 0;
  padding: 0;
  list-style: none;
}

.agenda-list li {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem 1rem;
  padding: 1rem 0;

  border-bottom: 1px solid var(--border-color, #e2e2eb);
  color: var(--text-muted, #666780);

  font-size: 0.95rem;
  line-height: 1.6;
}

.agenda-list li:first-child {
  border-top: 1px solid var(--border-color, #e2e2eb);
}

.agenda-list li strong {
  flex: 0 0 100px;
  color: var(--text-main, #1c1948);
  font-weight: 700;
}

/* ===== KARTU REGISTRASI ===== */
.sidebar {
  width: 100%;
}

.ticket-card {
  padding: 1.75rem;
  text-align: center;
}

.ticket-card h3 {
  margin: 0 0 1.25rem;
  color: var(--text-main, #1c1948);

  font-size: 1.2rem;
  font-weight: 700;
  line-height: 1.4;
}

.price {
  margin: 0 0 0.5rem;
  color: var(--primary, #6644ff);

  font-size: 2.8rem;
  font-weight: 800;
  line-height: 1.2;
}

.ticket-desc {
  margin: 0 0 1.5rem;
  color: var(--text-muted, #666780);

  font-size: 0.9rem;
  line-height: 1.7;
}

/* AppButton tetap digunakan */

.btn-register {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  min-height: 48px;
  padding: 12px 20px;
  background-color: #6644ff;
  color: #ffffff;
  border: none;
  border-radius: 12px;
  font-size: 16px;
  font-weight: 600;
  text-align: center;
  cursor: pointer;
  box-shadow: 0 6px 18px rgba(102, 68, 255, 0.2);
  transition:
    background-color 0.2s ease,
    transform 0.2s ease;
}

.btn-register:hover {
  background-color: #5232e8;
  transform: translateY(-2px);
}

.btn-register:active {
  transform: translateY(0);
}

.btn-register:focus-visible {
  outline: 3px solid rgba(102, 68, 255, 0.35);
  outline-offset: 3px;
}

/* ===== TABLET ===== */
@media (max-width: 900px) {
  .detail-content {
    grid-template-columns: minmax(0, 1fr) 280px;
    gap: 1.25rem;
  }

  .detail-header {
    padding: 2rem;
  }

  .ticket-card {
    padding: 1.5rem;
  }
}

/* ===== MOBILE ===== */
@media (max-width: 680px) {
  .event-detail-page {
    padding-bottom: 2rem;
  }

  .detail-header {
    padding: 1.5rem;
    border-radius: 12px;
  }

  .detail-header h1 {
    font-size: 1.8rem;
  }

  .meta-info {
    flex-direction: column;
    gap: 0.75rem;
  }

  .detail-content {
    grid-template-columns: minmax(0, 1fr);
    gap: 1.5rem;
  }

  .main-desc h2 {
    font-size: 1.3rem;
  }

  .agenda-list li strong {
    flex-basis: 90px;
  }

  .ticket-card {
    padding: 1.5rem;
  }

  .price {
    font-size: 2.4rem;
  }
}
</style>
