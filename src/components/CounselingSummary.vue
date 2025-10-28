<template>
  <div class="dashboard-card summary-card">
    <div class="card-header">
      <h2>Counseling Summary</h2>
      <button class="menu-btn" @click="handleClick" aria-label="View details">
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
          <circle cx="12" cy="6" r="2"/>
          <circle cx="12" cy="12" r="2"/>
          <circle cx="12" cy="18" r="2"/>
        </svg>
      </button>
    </div>

    <div class="stats-container">
      <div class="stat-item">
        <span class="stat-value">12</span>
        <span class="stat-label">Total Sessions</span>
      </div>
      <div class="stat-item">
        <span class="stat-value">45<small>min</small></span>
        <span class="stat-label">Average Duration</span>
      </div>
      <div class="stat-item">
        <span class="stat-value">3</span>
        <span class="stat-label">This Month</span>
      </div>
    </div>

    <div class="upcoming-sessions">
      <h3>Upcoming Sessions</h3>
      <ul class="session-list">
        <li v-for="session in upcomingSessions" :key="session.id" class="session-item">
          <span class="counselor">{{ session.counselor }}</span>
          <span class="date-time">{{ formatDateTime(session.date, session.time) }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const emit = defineEmits(['show-details'])

const handleClick = () => {
  emit('show-details')
}

const upcomingSessions = ref([
  { id: 1, counselor: 'Dr. Sarah Johnson', date: '2024-01-15', time: '14:00' },
  { id: 2, counselor: 'Dr. Michael Chen', date: '2024-01-20', time: '10:30' }
])

const formatDateTime = (date, time) => {
  const options = { month: 'short', day: 'numeric' }
  const formattedDate = new Date(date).toLocaleDateString('en-US', options)
  return `${formattedDate}, ${time}`
}
</script>

<style scoped>
.stats-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0.5rem;
  margin: 1.5rem 0;
  text-align: center;
}

.stat-item {
  padding: 0.5rem;
}

.stat-value {
  display: block;
  font-size: 2.25rem;
  font-weight: 700;
  color: var(--soft-crimson);
  line-height: 1;
  margin-bottom: 0.5rem;
}

@media (max-width: 768px) {
  .stats-container {
    grid-template-columns: repeat(3, 1fr); /* Keep 3 columns */
    gap: 0.25rem; /* Reduce gap for mobile */
    margin: 1rem 0; /* Adjust vertical margins */
  }

  .stat-item {
    padding: 0.25rem;
  }

  .stat-value {
    font-size: 1.75rem; /* Slightly smaller font */
    margin-bottom: 0.25rem;
  }

  .stat-label {
    font-size: 0.8rem; /* Smaller label text */
    line-height: 1.2;
  }
}

.stat-value small {
  font-size: 1rem;
  font-weight: 600;
  margin-left: 0.25rem;
}

.stat-label {
  font-size: 0.9rem;
  color: var(--charcoal-gray);
  opacity: 0.8;
}

.upcoming-sessions {
  margin-top: 2rem;
  border-top: 1px solid var(--light-beige);
  padding-top: 1rem;
}

.upcoming-sessions h3 {
  font-size: 1rem;
  margin-bottom: 0.75rem;
  color: var(--charcoal-gray);
}

.session-list {
  list-style: none;
  padding: 0;
}

.session-item {
  display: grid;
  grid-template-columns: 1fr auto;
  gap: 1rem;
  padding: 0.75rem 0;
  border-bottom: 1px solid var(--light-beige);
}

.session-item:last-child {
  border-bottom: none;
}

.counselor {
  font-weight: 600;
  color: var(--charcoal-gray);
}

.date-time {
  color: var(--soft-crimson);
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
}

.menu-btn {
  background: none;
  border: none;
  color: var(--charcoal-gray);
  padding: 0.5rem;
  cursor: pointer;
  border-radius: 50%;
  transition: background-color 0.2s ease;
  line-height: 0;
}

.menu-btn:hover {
  background-color: var(--light-beige);
  color: var(--soft-crimson);
}

.summary-card {
  cursor: default;
}

.summary-card:hover {
  transform: none;
  box-shadow: var(--shadow-soft);
}
</style>