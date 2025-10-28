<template>
  <div class="popup-overlay" @click.self="$emit('close')">
    <div class="popup-container">
      <button class="close-btn" @click="$emit('close')">&times;</button>
      
      <div class="popup-content">
        <h2>Counseling Details</h2>
        
        <div class="stats-grid">
          <div class="stat-card">
            <h3>Session Statistics</h3>
            <ul>
              <li>Total Sessions: <strong>12</strong></li>
              <li>Completed: <strong>9</strong></li>
              <li>Upcoming: <strong>3</strong></li>
              <li>Average Duration: <strong>45 min</strong></li>
            </ul>
          </div>
          
          <div class="stat-card">
            <h3>Monthly Overview</h3>
            <ul>
              <li>This Month: <strong>3 sessions</strong></li>
              <li>Last Month: <strong>4 sessions</strong></li>
              <li>Most Active Day: <strong>Tuesday</strong></li>
            </ul>
          </div>
        </div>

        <div class="sessions-section">
          <h3>Recent & Upcoming Sessions</h3>
          <div class="sessions-table">
            <table>
              <thead>
                <tr>
                  <th>Date</th>
                  <th>Time</th>
                  <th>Counselor</th>
                  <th>Type</th>
                  <th>Status</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="session in sessions" :key="session.id">
                  <td>{{ formatDate(session.date) }}</td>
                  <td>{{ session.time }}</td>
                  <td>{{ session.counselor }}</td>
                  <td>{{ session.type }}</td>
                  <td><span :class="['status', session.status]">{{ session.status }}</span></td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

defineEmits(['close'])

const sessions = ref([
  { id: 1, date: '2024-01-15', time: '14:00', counselor: 'Dr. Sarah Johnson', type: 'Online', status: 'upcoming' },
  { id: 2, date: '2024-01-20', time: '10:30', counselor: 'Dr. Michael Chen', type: 'In-Person', status: 'upcoming' },
  { id: 3, date: '2024-01-05', time: '15:00', counselor: 'Dr. Sarah Johnson', type: 'Online', status: 'completed' },
  { id: 4, date: '2023-12-28', time: '11:00', counselor: 'Dr. Emily Rodriguez', type: 'Online', status: 'completed' }
])

const formatDate = (date) => {
  return new Date(date).toLocaleDateString('en-US', {
    weekday: 'short',
    month: 'short',
    day: 'numeric'
  })
}
</script>

<style scoped>
.popup-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
  backdrop-filter: blur(8px);
}

.popup-container {
  background: rgba(255, 255, 255, 0.9);
  backdrop-filter: blur(10px);
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
  width: 90%;
  max-width: 900px;
  border-radius: var(--border-radius-lg);
  padding: 2rem;
  position: relative;
  max-height: 90vh;
  overflow-y: auto;
}

.close-btn {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: none;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
  color: var(--charcoal-gray);
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
  margin: 1.5rem 0;
}

.stat-card {
  background: var(--light-beige);
  padding: 1.5rem;
  border-radius: var(--border-radius-md);
}

.stat-card h3 {
  margin-bottom: 1rem;
  font-size: 1.1rem;
}

.stat-card ul {
  list-style: none;
  padding: 0;
}

.stat-card li {
  margin-bottom: 0.5rem;
  color: var(--charcoal-gray);
}

.sessions-section {
  margin-top: 2rem;
}

.sessions-table {
  margin-top: 1rem;
  overflow-x: auto;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  padding: 1rem;
  text-align: left;
  border-bottom: 1px solid var(--light-beige);
}

th {
  font-weight: 600;
  background: var(--light-beige);
}

.status {
  padding: 0.25rem 0.5rem;
  border-radius: var(--border-radius-sm);
  font-size: 0.9rem;
}

.status.upcoming {
  background: #E3F2FD;
  color: #1976D2;
}

.status.completed {
  background: #E8F5E9;
  color: #388E3C;
}
</style>
