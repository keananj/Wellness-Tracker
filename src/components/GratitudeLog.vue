<template>
  <div class="dashboard-card gratitude-log-card">
    <h2>Gratitude Log</h2>
    <p class="prompt">What are you thankful for today?</p>
    <textarea
      v-model="note"
      rows="3"
      placeholder="Today, I am grateful for..."
    ></textarea>
    <button @click="saveNote">Save Note</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const note = ref('')

const saveNote = () => {
  if (!note.value) return;
  // Di aplikasi nyata, Anda akan mengirim ini ke backend
  alert('Note Saved: "' + note.value + '"');
  note.value = ''; // Kosongkan setelah disimpan
}
</script>

<style scoped>
.prompt {
  font-size: 0.9rem;
  margin-bottom: 0.75rem;
  opacity: 0.9;
}

textarea {
  width: 100%;
  min-height: 100px;
  max-height: 200px;
  padding: 1rem;
  line-height: 1.5;
  border: 1px solid var(--light-beige);
  border-radius: var(--border-radius-md);
  font-family: 'Nunito', sans-serif;
  font-size: 1rem;
  resize: vertical;
  margin-bottom: 1rem;
}

textarea:focus {
  outline: none;
  border-color: var(--soft-crimson);
  box-shadow: 0 0 0 2px var(--light-beige);
}

button {
  width: auto;
  min-width: 120px;
  margin-left: auto;
  display: block;
  border: none;
  background-color: var(--soft-crimson);
  color: white;
  padding: 0.75rem;
  font-size: 1rem;
  font-weight: 700;
  border-radius: var(--border-radius-md);
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: var(--deep-red);
}

@media (max-width: 768px) {
  button {
    width: 100%;
  }

  textarea {
    min-height: 80px;
  }
}
</style>