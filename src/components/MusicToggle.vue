<template>
  <button 
    class="music-toggle-btn" 
    @click="$emit('toggle')"
    :aria-label="isPlaying ? 'Pause calm music' : 'Play calm music'"
  >
    <span class="icon">{{ isPlaying ? '🔇' : '🎵' }}</span>
  </button>
</template>

<script setup>
defineProps({
  isPlaying: Boolean
})
defineEmits(['toggle'])
</script>

<style scoped>
.music-toggle-btn {
  position: fixed;
  bottom: 2rem;
  right: 2rem;
  width: 56px;
  height: 56px;
  background-color: var(--deep-red);
  color: white;
  border: none;
  border-radius: 50%;
  font-size: 1.5rem;
  display: flex;
  justify-content: center;
  align-items: center;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  cursor: pointer;
  transition: transform 0.3s ease, background-color 0.3s ease;
  z-index: 200;
}

.music-toggle-btn:hover {
  transform: scale(1.1);
  background-color: var(--soft-crimson);
}

.icon {
  line-height: 0;
}
</style>