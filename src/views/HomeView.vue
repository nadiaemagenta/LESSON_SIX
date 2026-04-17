<script setup lang="ts">
import { ref, onMounted } from 'vue'

const isDark = ref(false)

function toggleTheme() {
  isDark.value = !isDark.value
  document.documentElement.classList.toggle('dark', isDark.value)
}

onMounted(() => {
  isDark.value = document.documentElement.classList.contains('dark')
})

const links = [
  { label: 'Portfolio', url: 'https://example.com/portfolio', icon: '🎨' },
  { label: 'LinkedIn', url: 'https://linkedin.com', icon: '💼' },
  { label: 'Email', url: 'mailto:nadia@example.com', icon: '✉️' },
]
</script>

<template>
  <div class="card">
    <button class="theme-toggle" @click="toggleTheme" :aria-label="isDark ? 'Switch to light mode' : 'Switch to dark mode'">
      {{ isDark ? '☀️' : '🌙' }}
    </button>

    <div class="avatar">
      <span class="avatar-placeholder">NM</span>
    </div>

    <h1 class="name">Nadia Magenta</h1>
    <p class="tagline">Developer · Designer · Creator</p>

    <div class="links">
      <a
        v-for="link in links"
        :key="link.label"
        :href="link.url"
        class="link-btn"
        target="_blank"
        rel="noopener noreferrer"
      >
        <span class="link-icon">{{ link.icon }}</span>
        {{ link.label }}
      </a>
    </div>
  </div>
</template>

<style scoped>
.card {
  width: 100%;
  max-width: 480px;
  background: var(--bg-card);
  border-radius: 24px;
  padding: 2.5rem 2rem;
  box-shadow: 0 4px 24px var(--shadow);
  text-align: center;
  position: relative;
  transition: background-color 0.3s, box-shadow 0.3s;
}

.theme-toggle {
  position: absolute;
  top: 1.25rem;
  right: 1.25rem;
  background: var(--toggle-bg);
  border: none;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  font-size: 1.2rem;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background-color 0.3s, transform 0.2s;
}

.theme-toggle:hover {
  transform: scale(1.1);
}

.avatar {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  margin: 0 auto 1.25rem;
  background: linear-gradient(135deg, #e040fb, #536dfe);
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.avatar-placeholder {
  color: #fff;
  font-size: 2rem;
  font-weight: 700;
  letter-spacing: 1px;
}

.name {
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 0.25rem;
  color: var(--text);
}

.tagline {
  color: var(--text-secondary);
  font-size: 0.95rem;
  margin-bottom: 2rem;
}

.links {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.link-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  padding: 0.875rem 1.5rem;
  background: var(--btn-bg);
  color: var(--btn-text);
  border-radius: 12px;
  text-decoration: none;
  font-weight: 500;
  font-size: 1rem;
  transition: background-color 0.25s, transform 0.2s, box-shadow 0.25s;
}

.link-btn:hover {
  background: var(--btn-hover-bg);
  color: var(--btn-hover-text);
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(224, 64, 251, 0.3);
}

.link-btn:active {
  transform: translateY(0);
}

.link-icon {
  font-size: 1.1rem;
}
</style>
