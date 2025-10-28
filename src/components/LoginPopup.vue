<template>
  <div class="login-overlay" @click.self="$emit('close')">
    <div class="login-container">
      <button class="close-btn" @click="$emit('close')">&times;</button>
      
      <div class="login-content">
        <h2>Member Login</h2>
        
        <form @submit.prevent="handleSubmit" class="login-form">
          <div class="form-group">
            <label for="email">Email Address</label>
            <input 
              type="email" 
              id="email" 
              v-model="email" 
              required
              placeholder="Enter your email"
            >
          </div>

          <div class="form-group">
            <label for="password">Password</label>
            <div class="password-input">
              <input 
                :type="showPassword ? 'text' : 'password'"
                id="password" 
                v-model="password" 
                required
                placeholder="Enter your password"
              >
              <button 
                type="button" 
                class="toggle-password"
                @click="showPassword = !showPassword"
              >
                👁️
              </button>
            </div>
            <a href="#" class="forgot-link">Forgot password?</a>
          </div>

          <button type="submit" class="login-btn">Log In</button>
        </form>

        <div class="divider">
          <span>or</span>
        </div>

        <div class="social-login">
          <button class="google-btn">
            <img src="/google-icon.png" alt="Google">
            Continue with Google
          </button>
          <button class="facebook-btn">
            <img src="/facebook-icon.png" alt="Facebook">
            Continue with Facebook
          </button>
        </div>

        <p class="signup-prompt">
          Not a member yet? <a href="#">Sign up now!</a>
        </p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

defineEmits(['close'])

const email = ref('')
const password = ref('')
const showPassword = ref(false)

const handleSubmit = () => {
  console.log('Login attempt:', { email: email.value, password: password.value })
}
</script>

<style scoped>
.login-overlay {
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

.login-container {
  background: rgba(255, 255, 255, 0.9);
  backdrop-filter: blur(10px);
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
  width: 90%;
  max-width: 400px;
  border-radius: var(--border-radius-lg);
  padding: 2rem;
  position: relative;
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

.login-content h2 {
  text-align: center;
  margin-bottom: 2rem;
  color: var(--charcoal-gray);
  font-size: 1.5rem;
  font-weight: 700;
  font-family: 'Nunito', sans-serif;
}

.login-form {
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
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--charcoal-gray);
  font-family: 'Nunito', sans-serif;
}

.form-group input {
  padding: 0.75rem;
  border: 1px solid var(--light-beige);
  border-radius: var(--border-radius-md);
  font-size: 0.95rem;
  font-family: 'Nunito', sans-serif;
  width: 100%;
}

.form-group input:focus {
  outline: none;
  border-color: var(--soft-crimson);
  box-shadow: 0 0 0 2px var(--light-beige);
}

.password-input {
  position: relative;
  display: flex;
  align-items: center;
  width: 100%;
}

.password-input input {
  padding-right: 2.5rem; /* Space for the eye icon */
}

.toggle-password {
  position: absolute;
  right: 0.75rem;
  background: none;
  border: none;
  cursor: pointer;
  padding: 0.25rem;
  font-size: 1rem;
  color: var(--charcoal-gray);
  opacity: 0.7;
  transition: opacity 0.2s ease;
}

.toggle-password:hover {
  opacity: 1;
}

.forgot-link {
  font-size: 0.85rem;
  color: var(--soft-crimson);
  text-decoration: none;
  align-self: flex-end;
}

.login-btn {
  background: var(--soft-crimson);
  color: white;
  border: none;
  padding: 0.75rem;
  border-radius: var(--border-radius-md);
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.3s ease;
  font-family: 'Nunito', sans-serif;
  font-size: 0.95rem;
}

.login-btn:hover {
  background: var(--deep-red);
}

.divider {
  margin: 1.5rem 0;
  display: flex;
  align-items: center;
  text-align: center;
}

.divider::before,
.divider::after {
  content: '';
  flex: 1;
  border-bottom: 1px solid var(--light-beige);
}

.divider span {
  padding: 0 1rem;
  color: var(--charcoal-gray);
  font-size: 0.9rem;
}

.social-login {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.social-login button {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.75rem;
  padding: 0.75rem;
  border: 1px solid var(--light-beige);
  border-radius: var(--border-radius-md);
  background: white;
  cursor: pointer;
  transition: background-color 0.3s ease;
  font-family: 'Nunito', sans-serif;
  font-size: 0.95rem;
  font-weight: 600;
}

.social-login img {
  width: 20px;
  height: 20px;
}

.signup-prompt {
  margin-top: 1.5rem;
  text-align: center;
  font-size: 0.9rem;
}

.signup-prompt a {
  color: var(--soft-crimson);
  text-decoration: none;
  font-weight: 600;
}

@media (max-width: 768px) {
  .login-container {
    padding: 1.5rem;
  }

  .social-login button {
    padding: 0.5rem;
  }
}
</style>
