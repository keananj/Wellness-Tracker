<template>
  <div class="dashboard-card counseling-card">
    <h2>Counseling Sessions</h2>
    <div class="content">
      <div class="status-section">
        <div class="status-icon">📅</div>
        <div class="status-info">
          <p class="next-session">Next Session</p>
          <p class="session-date">Not scheduled</p>
        </div>
      </div>

      <div class="sessions-info">
        <div class="info-row">
          <span class="info-label">Last Session</span>
          <span class="info-value">Dec 15, 2023</span>
        </div>
        <div class="info-row">
          <span class="info-label">Counselor</span>
          <span class="info-value">Dr. Sarah Johnson</span>
        </div>
        <div class="info-row">
          <span class="info-label">Type</span>
          <span class="info-value highlight">Online</span>
        </div>
      </div>

      <button class="schedule-btn" @click="$emit('open-counseling')">
        Schedule Session
      </button>
    </div>
  </div>
</template>

<style scoped>
.counseling-card {
  background-color: var(--white);
  display: flex;
  flex-direction: column;
}

.content {
  margin-top: 0.5rem;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.status-section {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1rem;
  background: var(--light-beige);
  border-radius: var(--border-radius-md);
}

.status-icon {
  font-size: 1.5rem;
  color: var(--soft-crimson);
}

.status-info {
  flex-grow: 1;
}

.next-session {
  font-size: 0.9rem;
  color: var(--charcoal-gray);
  opacity: 0.8;
  margin-bottom: 0.25rem;
}

.session-date {
  font-weight: 600;
  color: var(--charcoal-gray);
}

.schedule-btn {
  width: 100%;
  background-color: var(--soft-crimson);
  color: var(--white);
  border: none;
  padding: 0.75rem;
  border-radius: var(--border-radius-md);
  cursor: pointer;
  font-weight: 600;
  font-size: 0.95rem;
  transition: background-color 0.3s ease;
}

.schedule-btn:hover {
  background-color: var(--deep-red);
}

.quick-info {
  margin: 0.5rem 0;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.info-item {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.9rem;
  color: var(--charcoal-gray);
}

.info-icon {
  color: var(--soft-crimson);
  font-size: 0.85rem;
}

.highlight {
  font-weight: 600;
  color: var(--soft-crimson);
}

.sessions-info {
  background: var(--light-beige);
  border-radius: var(--border-radius-md);
  padding: 0.75rem 1rem;
}

.info-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.5rem 0;
  font-size: 0.9rem;
  border-bottom: 1px solid rgba(0, 0, 0, 0.05);
}

.info-row:last-child {
  border-bottom: none;
}

.info-label {
  color: var(--charcoal-gray);
  opacity: 0.8;
}

.info-value {
  font-weight: 600;
  color: var(--charcoal-gray);
}

.highlight {
  color: var(--soft-crimson);
}

.tip-section {
  background-color: var(--light-beige);
  border-radius: var(--border-radius-sm);
  padding: 0.75rem;
  margin-bottom: 1rem;
}

.tip-text {
  font-size: 0.9rem;
  font-style: italic;
  color: var(--charcoal-gray);
  text-align: center;
  opacity: 0.9;
}

@media (max-width: 768px) {
  .content {
    gap: 1rem;
  }
  
  .status-section {
    padding: 0.75rem;
  }
  
  .quick-info {
    margin: 0.75rem 0;
  }
  
  .tip-section {
    padding: 0.5rem;
  }
}
</style>