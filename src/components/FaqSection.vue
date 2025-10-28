<template>
  <section class="faq-section">
    <div class="faq-container">
      <h2 class="faq-title">Q&A</h2>
      
      <div class="faq-list">
        <div 
          v-for="(faq, index) in faqs" 
          :key="index" 
          class="faq-item" 
          :class="{ 'is-open': faq.isOpen }"
        >
          <button class="faq-question" @click="toggleFaq(index)">
            <span>{{ faq.question }}</span>
            <svg class="faq-icon" xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
              <polyline points="6 9 12 15 18 9"></polyline>
            </svg>
          </button>
          
          <transition name="expand">
            <div v-show="faq.isOpen" class="faq-answer">
              <p>{{ faq.answer }}</p>
            </div>
          </transition>
        </div>
      </div>

    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

// State untuk daftar Q&A
const faqs = ref([
  {
    question: "What is EmergencyyCall?",
    answer: "EmergencyyCall is a community platform that focuses on mental health as a primary foundation for self-development. We provide tools like mood tracking, journaling, and access to counseling to help you on your wellness journey.",
    isOpen: true
  },
  {
    question: "Is this a replacement for therapy?",
    answer: "No. While EmergencyyCall provides supportive tools and access to professionals, it is not intended to replace professional medical advice, diagnosis, or treatment. Always seek the advice of your mental health professional or other qualified health provider with any questions.",
    isOpen: false
  },
  {
    question: "How do I schedule a counseling session?",
    answer: "You can schedule a session by clicking the 'Counseling' link in the main navigation (or the 'Manage Sessions' card). This will open your counseling dashboard where you can select a professional, pick an available date and time, and add a note for your session.",
    isOpen: false
  },
  {
    question: "Is my Gratitude Log private?",
    answer: "<strong>Yes.</strong> Your Gratitude Log and personal mood data are private to your account. We prioritize your privacy and provide a safe space for your personal reflections.",
    isOpen: false
  }
])

// Fungsi untuk membuka/menutup FAQ
const toggleFaq = (index) => {
  faqs.value[index].isOpen = !faqs.value[index].isOpen
}
</script>

<style scoped>
.faq-section {
  padding: 3rem 2rem;
  background-color: var(--cream-white);
}

.faq-container {
  max-width: 800px;
  margin: 0 auto;
}

.faq-title {
  text-align: center;
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 2.5rem;
  color: var(--charcoal-gray);
}

.faq-list {
  border: 1px solid var(--light-beige);
  border-radius: var(--border-radius-lg);
  background-color: var(--white);
  box-shadow: var(--shadow-soft);
  overflow: hidden; /* Penting untuk rounded corners */
}

.faq-item {
  border-bottom: 1px solid var(--light-beige);
}
.faq-item:last-child {
  border-bottom: none;
}

.faq-question {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 1.5rem;
  border: none;
  background: none;
  cursor: pointer;
  text-align: left;
  font-family: 'Nunito', sans-serif;
  font-size: 1.1rem;
  font-weight: 600;
  color: var(--charcoal-gray);
}

.faq-question:hover {
  background-color: var(--cream-white);
}

.faq-icon {
  color: var(--soft-crimson);
  transition: transform 0.3s ease;
  flex-shrink: 0; /* Mencegah ikon mengecil */
  margin-left: 1rem;
}

.faq-item.is-open .faq-icon {
  transform: rotate(180deg);
}

.faq-answer {
  padding: 0 1.5rem 1.5rem 1.5rem;
  line-height: 1.7;
  color: var(--charcoal-gray);
  opacity: 0.9;
}

/* Transisi untuk expand/collapse */
.expand-enter-active,
.expand-leave-active {
  transition: grid-template-rows 0.3s ease, opacity 0.3s ease;
  grid-template-rows: 1fr;
  opacity: 1;
}

.expand-enter-from,
.expand-leave-to {
  grid-template-rows: 0fr;
  opacity: 0;
  /* Atur padding untuk mencegah 'jump' */
  padding-top: 0;
  padding-bottom: 0;
  margin-top: 0;
  margin-bottom: 0;
}

/* Wrapper untuk transisi yang lebih mulus */
.faq-answer {
  display: grid;
  grid-template-rows: 0fr;
  transition: grid-template-rows 0.3s ease;
}
.faq-answer p {
  overflow: hidden;
}
.faq-item.is-open .faq-answer {
  grid-template-rows: 1fr;
}

</style>
