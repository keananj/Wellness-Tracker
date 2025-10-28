<template>
  <div class="counseling-overlay" @click.self="$emit('close')">
    <div class="counseling-container">
      <button class="close-btn" @click="$emit('close')" aria-label="Close counseling page">×</button>

      <div class="counseling-content">
        <h2>Schedule Management</h2>
        
        <div class="counseling-form">
          <div class="form-group">
            <label for="counselor">Select Counselor</label>
            <select id="counselor" v-model="formData.counselor">
              <option value="">Choose a counselor</option>
              <option v-for="counselor in counselors" :key="counselor.id" :value="counselor.name">
                {{ counselor.name }}
              </option>
            </select>
          </div>

          <div class="form-group">
            <label for="date">Preferred Date</label>
            <input type="date" id="date" v-model="formData.date">
          </div>

          <div class="form-group">
            <label for="time">Preferred Time</label>
            <input type="time" id="time" v-model="formData.time">
          </div>

          <div class="form-group">
            <label for="notes">Additional Notes</label>
            <textarea id="notes" v-model="formData.notes" rows="4" placeholder="Briefly describe what you'd like to discuss..."></textarea>
          </div>

          <button class="submit-btn" @click="submitForm">Schedule Session</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const counselors = [
  { id: 1, name: 'Dr. Sarah Johnson' },
  { id: 2, name: 'Dr. Michael Chen' },
  { id: 3, name: 'Dr. Emily Rodriguez' }
]

const formData = ref({
  counselor: '',
  date: '',
  time: '',
  notes: ''
})

const submitForm = () => {
  // Here you would typically handle form submission
  console.log('Form submitted:', formData.value)
  // Emit close event after successful submission
  emit('close')
}

const emit = defineEmits(['close'])
</script>

<style scoped>
.counseling-overlay {
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

.counseling-container {
  background: rgba(255, 255, 255, 0.9);
  backdrop-filter: blur(10px);
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
  width: 90%;
  max-width: 600px;
  border-radius: var(--border-radius-lg);
  position: relative;
  padding: 2rem;
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

.counseling-content h2 {
  color: var(--charcoal-gray);
  margin-bottom: 2rem;
  font-size: 1.5rem;
}

.counseling-form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.form-group label {
  font-weight: 600;
  color: var(--charcoal-gray);
}

.form-group input,
.form-group select,
.form-group textarea {
  padding: 0.75rem;
  border: 1px solid var(--light-beige);
  border-radius: var(--border-radius-md);
  font-family: inherit;
}

.submit-btn {
  background: var(--soft-crimson);
  color: white;
  border: none;
  padding: 1rem;
  border-radius: var(--border-radius-md);
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.submit-btn:hover {
  background: var(--deep-red);
}
</style>
