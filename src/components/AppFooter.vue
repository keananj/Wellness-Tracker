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

.footer-copyright {
  font-size: 0.85rem;
  color: var(--cream-white);
  opacity: 0.7;
}
</style>