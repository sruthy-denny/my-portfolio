<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { ref, onMounted, onUnmounted } from 'vue'

const menuOpen = ref(false)
const base = import.meta.env.BASE_URL

function closeMenu(event) {
  if (!event.target.closest('header')) {
    menuOpen.value = false
  }
}

onMounted(() => document.addEventListener('click', closeMenu))
onUnmounted(() => document.removeEventListener('click', closeMenu))
</script>

<template>
  <header>
    <RouterLink to="/" class="logo">SD</RouterLink>
    <button class="menu-button" aria-label="Open menu" @click="menuOpen = !menuOpen">
    <span></span>
    <span></span>
    </button>
      <nav v-if="menuOpen" @click="menuOpen = false">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/experience">Experience</RouterLink>
        <RouterLink to="/projects">Experiments</RouterLink>
        <RouterLink to="/contact">Contact</RouterLink>
        <a :href="base + 'Sruthy_Denny_Resume.pdf'" download>Resume</a>
      </nav>
  </header>

    <RouterView v-slot="{ Component, route }">
    <div :key="route.path" :class="{ 'page-fade': route.path !== '/' }">
    <component :is="Component" />
    </div>
    </RouterView>
</template>

<style scoped>
nav{
  position: absolute;
  top: 100%;
  right: 0;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  padding: 1rem 1.5rem;
  background: #fff7f2;
  border-radius: 12px;
}

.logo {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 56px;
  height: 56px;
  font-size: 18px;
  border-radius: 50%;
  background: #b5655f;
  color: #fff7f2;
  font-weight: 500;
}

.logo:hover {
   background: #fff7f2;
  color: #b5655f;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: relative;
  z-index: 10;
}

.menu-button {
  background: none;
  border: none;
  cursor: pointer;
  display: flex;
  flex-direction: column;
  gap: 6px;
  padding: 8px;
}

.menu-button span {
  display: block;
  width: 28px;
  height: 2px;
  background: #4a3b3b;
  transition: background 0.3s ease;
}

  .menu-button:hover span {
  background: #b5655f;
  }

@keyframes fade-up {
  from {
    opacity: 0;
    transform: translateY(14px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.page-fade {
  animation: fade-up 1s ease both;
}
</style>
