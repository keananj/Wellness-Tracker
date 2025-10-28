<template>
  <div class="popup-overlay" @click.self="$emit('close')">
    <div class="popup-container">
      <button class="close-btn" @click="$emit('close')">&times;</button>
      
      <div class="popup-content">
        <h2>Mood Analysis</h2>
        
        <div class="mood-insights">
          <div class="stat-card">
            <h3>Weekly Overview</h3>
            <div class="stat-grid">
              <div v-for="(mood, day) in weeklyMoods" :key="day" class="day-mood">
                <span class="day-label">{{ day }}</span>
                <span class="mood-emoji">{{ mood.emoji }}</span>
                <span class="mood-label" :style="{ color: mood.color }">
                  {{ mood.label }}
                </span>
              </div>
            </div>
          </div>

          <div class="insight-card">
            <h3>Insights</h3>
            <ul class="insight-list">
              <li>Most frequent mood: <strong>Calm</strong></li>
              <li>Mood improved after sessions</li>
              <li>Best day: <strong>Friday</strong></li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
defineEmits(['close'])

const weeklyMoods = {
  'Monday': { emoji: '😌', label: 'Calm', color: '#4CAF50' },
  'Tuesday': { emoji: '😊', label: 'Happy', color: '#2196F3' },
  'Wednesday': { emoji: '😰', label: 'Anxious', color: '#FF9800' },
  'Thursday': { emoji: '😌', label: 'Calm', color: '#4CAF50' },
  'Friday': { emoji: '😊', label: 'Happy', color: '#2196F3' }
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
  max-width: 600px;
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

.mood-insights {
  margin-top: 2rem;
  display: grid;
  gap: 2rem;
}

.stat-card, .insight-card {
  background: var(--light-beige);
  padding: 1.5rem;
  border-radius: var(--border-radius-md);
}

.stat-grid {
  display: grid;
  gap: 1rem;
  margin-top: 1rem;
}

.day-mood {
  display: grid;
  grid-template-columns: 1fr auto auto;
  gap: 1rem;
  align-items: center;
  padding: 0.5rem;
  background: white;
  border-radius: var(--border-radius-sm);
}

.day-label {
  font-weight: 600;
}

.mood-emoji {
  font-size: 1.25rem;
}

.mood-label {
  font-weight: 500;
}

.insight-list {
  margin-top: 1rem;
  list-style: none;
  padding: 0;
}

.insight-list li {
  margin-bottom: 0.75rem;
  padding-left: 1.5rem;
  position: relative;
}

.insight-list li::before {
  content: "•";
  position: absolute;
  left: 0;
  color: var(--soft-crimson);
}

@media (max-width: 768px) {
  .popup-container {
    padding: 1.5rem;
  }
  
  .day-mood {
    gap: 0.5rem;
  }
}
</style>
