<template>
  <header class="app-header">
    <nav class="nav-container">
      
      <div class="logo">
        <img src="/Emergencycall.png" alt="Emergency Call Logo" class="logo-image">
        Emergencyy<span class="logo-accent">Call</span>
      </div>

      <div class="nav-icons-right">
        <a href="#" class="profile-icon" @click.prevent="isLoginOpen = true" aria-label="Profile Page">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"></path>
            <circle cx="12" cy="7" r="4"></circle>
          </svg>
        </a>
      </div>

    </nav>
  </header>

  <transition name="fade">
    <LoginPopup v-if="isLoginOpen" @close="isLoginOpen = false" />
  </transition>
</template>

<script setup>
import { ref } from 'vue'
import LoginPopup from './LoginPopup.vue'

const isLoginOpen = ref(false)
</script>

<style scoped>
.app-header {
  width: 100%;
  background-color: var(--white);
  box-shadow: var(--shadow-soft);
  padding: 1rem 2rem;
  position: sticky;
  top: 0;
  z-index: 100;

  font-family: 'Nunito', sans-serif;
}

.nav-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
}

.logo {
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--charcoal-gray);
  flex-shrink: 0;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.logo-image {
  height: 30px;
  width: auto;
  object-fit: contain;
}

.logo-accent {
  color: var(--soft-crimson);
}

/* Navigasi Desktop */
.nav-links-desktop {
  display: none; /* Sembunyikan di seluler secara default */
  list-style: none;
  gap: 2rem;
  margin: 0 auto; /* Pusatkan link di antara logo dan ikon */
}

.nav-links-desktop a {
  text-decoration: none;
  color: var(--charcoal-gray);
  font-weight: 600;
  padding-bottom: 0.25rem;
  border-bottom: 2px solid transparent;
  transition: color 0.3s ease, border-color 0.3s ease;
}

.nav-links-desktop a:hover {
  color: var(--soft-crimson);
}

.nav-links-desktop a.active {
  color: var(--deep-red);
  border-bottom-color: var(--deep-red);
}

/* Ikon Kanan */
.nav-icons-right {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.profile-icon {
  color: var(--charcoal-gray);
  transition: color 0.3s ease;
}
.profile-icon:hover {
  color: var(--soft-crimson);
}
.profile-icon svg {
  display: block; /* Menghapus spasi ekstra di bawah svg */
}

/* Menu Pop-over Seluler */
.mobile-nav-links {
  position: absolute;
  top: 100%;
  left: 0;
  right: 0;
  background-color: var(--white);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.07);
  border-bottom-left-radius: var(--border-radius-lg);
  border-bottom-right-radius: var(--border-radius-lg);
  overflow: hidden;
}

.mobile-nav-links ul {
  list-style: none;
  padding: 1rem 0;
}

.mobile-nav-links li a {
  display: block;
  padding: 1rem 2rem;
  text-decoration: none;
  color: var(--charcoal-gray);
  font-weight: 600;
  font-size: 1.1rem;
}
.mobile-nav-links li a:hover {
  background-color: var(--cream-white);
  color: var(--deep-red);
}

/* Transisi untuk menu seluler */
.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}
.slide-fade-leave-active {
  transition: all 0.3s cubic-bezier(1, 0.5, 0.8, 1);
}
.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateY(-20px);
  opacity: 0;
}


/* --- TAMPILAN DESKTOP (Media Query) --- */
@media (min-width: 768px) {
  .nav-links-desktop {
    display: flex; /* Tampilkan link nav desktop */
  }
  .mobile-menu-toggle {
    display: none; /* Sembunyikan tombol hamburger */
  }
}
</style>