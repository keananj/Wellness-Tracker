<template>
  <footer class="app-footer">
    <div class="footer-container">
      <div class="footer-logo">
        <img src="/Emergencycall.png" alt="Emergency Call Logo" class="logo-image">
        Emergencyy<span class="logo-accent">Call</span>
      </div>
      <div class="footer-links">
        <a href="#">Privacy Policy</a>
        <a href="#">Terms of Service</a>
        <a href="#">Contact Us</a>
      </div>

      <div class="footer-github-link">
        <a href="https://github.com/keananj/Wellness-Tracker/tree/main" target="_blank" rel="noopener noreferrer">
          <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
            <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.108-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.91 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.085 8.199-11.386 0-6.627-5.373-12-12-12z"/>
          </svg>
          <span>Check Out The Project On GitHub</span>
        </a>
      </div>
      <p class="footer-copyright">
        &copy; {{ new Date().getFullYear() }} EmergencyyCall. All rights reserved.
      </p>
    </div>
  </footer>
</template>

<style scoped>
.app-footer {
  background-color: var(--charcoal-gray);
  color: var(--cream-white);
  padding: 3rem 2rem;
  text-align: center;
}

.footer-container {
  max-width: 1200px;
  margin: 0 auto;
}

.footer-logo {
  font-size: 1.75rem;
  font-weight: 700;
  margin-bottom: 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
}

.logo-image {
  height: 35px;
  width: auto;
  object-fit: contain;
}

.logo-accent {
  color: var(--soft-crimson);
}

.footer-links {
  display: flex;
  justify-content: center;
  gap: 1.5rem;
  margin-bottom: 1.5rem;
}

.footer-links a {
  color: var(--light-beige);
  text-decoration: none;
  font-size: 0.9rem;
  transition: color 0.3s ease;
}

.footer-links a:hover {
  color: var(--white);
  text-decoration: underline;
}

/* KODE BARU DITAMBAHKAN DI SINI */
.footer-github-link {
  margin-bottom: 1.5rem;
  margin-top: 2rem; /* Memberi jarak dari link di atasnya */
}

.footer-github-link a {
  display: inline-flex; /* Membuat ikon dan teks sejajar */
  align-items: center;
  gap: 0.5rem; /* Jarak antara ikon dan teks */
  color: var(--light-beige);
  text-decoration: none;
  font-size: 0.9rem;
  transition: color 0.3s ease;
}

.footer-github-link a:hover {
  color: var(--white);
  text-decoration: underline;
}

.footer-github-link svg {
  fill: currentColor; /* Membuat SVG mengikuti warna teks */
}
/* AKHIR KODE BARU */

.footer-copyright {
  font-size: 0.85rem;
  color: var(--cream-white);
  opacity: 0.7;
}
</style>

