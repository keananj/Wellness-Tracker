<template>
  <div class="dashboard-card mood-tracker-card">
    <div class="card-header">
      <h2>Weekly Mood</h2>
      <button class="menu-btn" @click.stop="$emit('show-mood-details')" aria-label="View mood details">
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
          <circle cx="12" cy="6" r="2"/>
          <circle cx="12" cy="12" r="2"/>
          <circle cx="12" cy="18" r="2"/>
        </svg>
      </button>
    </div>

    <div class="chart-container">
      <svg class="mood-chart" viewBox="0 0 100 50">
        <rect x="10" y="20" width="10" height="30" rx="2"></rect>
        <rect x="30" y="30" width="10" height="20" rx="2"></rect>
        <rect x="50" y="10" width="10" height="40" rx="2"></rect>
        <rect x="70" y="15" width="10" height="35" rx="2"></rect>
        <rect x="90" y="5" width="10" height="45" rx="2"></rect>
      </svg>
    </div>
    
    <div class="chart-labels">
      <span>Mon</span>
      <span>Tue</span>
      <span>Wed</span>
      <span>Thu</span>
      <span>Fri</span>
    </div>

    <div class="mood-summary">
      <span class="trend">Mood trend: <span class="trend-positive">Improving</span></span>
    </div>
  </div>
</template>

<script setup>
defineEmits(['show-mood-details'])
</script>

<style scoped>
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
  transition: all 0.2s ease;
  line-height: 0;
}

.menu-btn:hover {
  background-color: var(--light-beige);
  color: var(--soft-crimson);
}

.chart-container {
  width: 100%;
  margin: 1rem 0;
}

.mood-chart {
  width: 100%;
  height: 100px;
}

.mood-chart rect {
  fill: var(--light-beige);
  transition: fill 0.3s ease;
}

.mood-chart rect:hover {
  fill: var(--soft-crimson);
}

.chart-labels {
  display: flex;
  justify-content: space-around;
  font-size: 0.8rem;
  color: var(--charcoal-gray);
  opacity: 0.7;
  padding: 0 5%;
}

.mood-summary {
  margin-top: 1rem;
  text-align: center;
  font-size: 0.9rem;
  color: var(--charcoal-gray);
}

.trend-positive {
  color: #4CAF50;
  font-weight: 600;
}
</style>