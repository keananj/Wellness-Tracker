<template>
  <div id="app-container" :class="{ 'blur-background': isCounselingPageOpen || isDetailsOpen || isLoginOpen }">
    <Header @open-counseling="isCounselingPageOpen = true" @login-state="isLoginOpen = $event" />

    <main class="dashboard-content">
      <div class="greeting-section">
        <div class="greeting-container">
          <h1 class="time-greeting">{{ greeting }}</h1>
          <p class="daily-quote">{{ randomMotivation }}</p>
        </div>
      </div>

      <div class="dashboard-grid">
        <!-- First Row -->
        <CounselingSummary class="grid-span-2" @show-details="isDetailsOpen = true" />
        <Counseling @open-counseling="isCounselingPageOpen = true" />
        <MoodTracker @show-mood-details="isMoodDetailsOpen = true" />
        <!-- Second Row -->
        <GratitudeLog class="grid-span-2" />
      </div>
    </main>

    <FaqSection />
    <AppFooter />
    <MusicToggle :isPlaying="isMusicPlaying" @toggle="isMusicPlaying = !isMusicPlaying" />
  </div>

  <transition name="fade">
    <CounselingPage 
      v-if="isCounselingPageOpen" 
      @close="isCounselingPageOpen = false" 
    />
  </transition>

  <transition name="fade">
    <SummaryDetailsPopup 
      v-if="isDetailsOpen" 
      @close="isDetailsOpen = false" 
    />
  </transition>

  <transition name="fade">
    <MoodDetailsPopup 
      v-if="isMoodDetailsOpen" 
      @close="isMoodDetailsOpen = false" 
    />
  </transition>
</template>

<script setup>
import { ref, onMounted } from 'vue'

// Update imports
import Header from './components/Header.vue'
import Counseling from './components/Counseling.vue'
import CounselingPage from './components/CounselingPage.vue'
import MoodTracker from './components/MoodTracker.vue'
import CounselingSummary from './components/CounselingSummary.vue'
import GratitudeLog from './components/GratitudeLog.vue'
import MusicToggle from './components/MusicToggle.vue'
import FaqSection from './components/FaqSection.vue'
import AppFooter from './components/AppFooter.vue'
import SummaryDetailsPopup from './components/SummaryDetailsPopup.vue'
import MoodDetailsPopup from './components/MoodDetailsPopup.vue'

// Add new state
const isCounselingPageOpen = ref(false)
const isDetailsOpen = ref(false)
const isMoodDetailsOpen = ref(false)
const isLoginOpen = ref(false)

// --- STATE MANAGEMENT SEDERHANA ---

// 1. State untuk Sapaan
const greeting = ref('Welcome back 👋')

// 2. State untuk Motivasi Harian
const randomMotivation = ref('')
const motivations = [
  "Your feelings are valid. Take your time.",
  "One small step, even a breath, is still progress.",
  "Be kind to your mind today. You're doing great.",
  "It's okay to not be okay. You are not alone.",
  "Embrace calmness, you deserve peace."
]

// 3. State untuk Toggle Musik
const isMusicPlaying = ref(false)

// --- LOGIC SAAT KOMPONEN DIMUAT ---
onMounted(() => {
  // Set Sapaan berdasarkan waktu
  const hour = new Date().getHours()
  if (hour < 12) {
    greeting.value = 'Good morning, take a deep breath'
  } else if (hour < 18) {
    greeting.value = 'Good afternoon, how are you feeling today?'
  } else {
    greeting.value = 'Good evening, time to unwind'
  }

  // Set Motivasi acak
  randomMotivation.value = motivations[Math.floor(Math.random() * motivations.length)]
})
</script>

<style>
/* --- GLOBAL STYLES & CSS VARIABLES --- */
:root {
  --deep-red: #B71C1C;
  --soft-crimson: #E53935;
  --light-beige: #e4e4e4ff;
  --cream-white: #f4f4f4ff;
  --charcoal-gray: #333333;
  --white: #FFFFFF;

  --border-radius-lg: 16px;
  --border-radius-md: 12px;
  --border-radius-sm: 8px;

  --shadow-soft: 0 4px 12px rgba(0, 0, 0, 0.05);
  --shadow-hover: 0 6px 16px rgba(0, 0, 0, 0.08);
}

/* Reset dasar dan font global */
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Nunito', -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  background-color: var(--cream-white);
  color: var(--charcoal-gray);
  line-height: 1.6;
}

/* --- APP LAYOUT --- */
#app-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.dashboard-content {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
  flex-grow: 1; /* Membuat konten tumbuh mengisi ruang */
}

.greeting-section {
  margin-bottom: 2.5rem;
  text-align: center;
  padding: 1rem;
}

.greeting-container {
  max-width: 800px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.5rem;
}

.time-greeting {
  font-size: 2.5rem;
  font-weight: 800;
  color: var(--charcoal-gray);
  line-height: 1.2;
}

.daily-quote {
  font-size: 1.25rem;
  font-weight: 600;
  font-style: italic;
  color: var(--soft-crimson);
  line-height: 1.4;
  max-width: 600px;
}

.dashboard-grid {
  display: grid;
  gap: 1.5rem;
}

/* Mobile styles (default) */
@media (max-width: 767px) {
  .dashboard-grid {
    grid-template-columns: 1fr;
  }

  .grid-span-2 {
    grid-column: auto; /* Reset span on mobile */
  }

  .dashboard-content {
    padding: 1rem;
  }

  .time-greeting {
    font-size: 1.75rem;
    margin-bottom: 1rem;
  }

  .daily-quote {
    font-size: 1rem;
  }

  .dashboard-card {
    padding: 1.25rem;
  }
}

/* Tablet styles */
@media (min-width: 768px) and (max-width: 991px) {
  .dashboard-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* Desktop styles */
@media (min-width: 992px) {
  .dashboard-grid {
    grid-template-columns: repeat(3, 1fr);
  }

  .grid-span-2 {
    grid-column: span 2;
  }

  .dashboard-content {
    padding: 2rem;
  }

  .time-greeting {
    font-size: 2.25rem;
  }
}

.dashboard-card {
  background-color: var(--white);
  border-radius: var(--border-radius-lg);
  padding: 1.5rem; /* 24px */
  box-shadow: var(--shadow-soft);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.dashboard-card:hover {
  transform: translateY(-4px);
  box-shadow: var(--shadow-hover);
}

.dashboard-card h2 {
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--charcoal-gray);
  margin-bottom: 1rem;
}

/* Add new transition styles */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

#app-container {
  transition: filter 0.3s ease;
}

#app-container.blur-background {
  filter: blur(5px);
  pointer-events: none;
  overflow: hidden;
}
</style>