<template>
  <div class="dashboard-card mindful-moment-card">
    <h2>Mindful Moment</h2>
    <div class="breathing-container">
      <div class="breathing-circle" :style="{ animationPlayState: animationState }"></div>
      <p class="breathing-text">{{ breathText }}</p>
    </div>
    <button @click="toggleAnimation" class="pause-button">
      {{ isPaused ? 'Resume' : 'Pause' }}
    </button>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const breathText = ref('Breathe In...')
const isPaused = ref(false)
const animationState = ref('running')
let timeout1, timeout2, timeout3;

const breathCycle = () => {
  breathText.value = 'Breathe In...'
  timeout1 = setTimeout(() => {
    breathText.value = 'Hold'
  }, 4000); // Durasi tarik napas

  timeout2 = setTimeout(() => {
    breathText.value = 'Exhale Slowly...'
  }, 6000); // Durasi tahan (4s + 2s)

  timeout3 = setTimeout(breathCycle, 10000); // Durasi total siklus (4s + 2s + 4s)
}

const toggleAnimation = () => {
  isPaused.value = !isPaused.value;
  animationState.value = isPaused.value ? 'paused' : 'running';
  
  // Logika untuk pause/resume timeout (disederhanakan)
  // Untuk implementasi penuh, Anda perlu melacak sisa waktu
  if (isPaused.value) {
    clearTimeout(timeout1);
    clearTimeout(timeout2);
    clearTimeout(timeout3);
  } else {
    breathCycle(); // Mulai ulang siklus saat resume
  }
}

onMounted(() => {
  breathCycle();
})

onUnmounted(() => {
  // Hentikan semua timeout saat komponen dihancurkan
  clearTimeout(timeout1);
  clearTimeout(timeout2);
  clearTimeout(timeout3);
})
</script>

<style scoped>
.mindful-moment-card {
  text-align: center;
  background: linear-gradient(135deg, var(--white), var(--cream-white));
}

.breathing-container {
  position: relative;
  width: 150px;
  height: 150px;
  margin: 2rem auto;
  display: flex;
  justify-content: center;
  align-items: center;
}

.breathing-circle {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  background-color: var(--light-beige);
  animation: breathe 10s infinite ease-in-out;
}

.breathing-text {
  position: absolute;
  font-size: 1.1rem;
  font-weight: 600;
  color: var(--charcoal-gray);
  opacity: 0.9;
}

.pause-button {
  font-family: 'Nunito', sans-serif;
  font-weight: 600;
  border: none;
  background-color: var(--light-beige);
  color: var(--charcoal-gray);
  padding: 0.5rem 1rem;
  border-radius: var(--border-radius-sm);
  cursor: pointer;
  transition: background-color 0.3s ease;
}
.pause-button:hover {
  background-color: #EADCD7; /* Versi lebih gelap dari light-beige */
}

/* Animasi Pernapasan */
@keyframes breathe {
  0% {
    transform: scale(0.8);
    opacity: 0.7;
  }
  40% { /* 4s Breathe In */
    transform: scale(1.1);
    opacity: 1;
  }
  60% { /* 2s Hold */
    transform: scale(1.1);
    opacity: 1;
  }
  100% { /* 4s Exhale */
    transform: scale(0.8);
    opacity: 0.7;
  }
}
</style>