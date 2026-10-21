<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const words = ['Frontend Enthusiast', 'Singer', 'Book lover', 'Trailblazer']
const index = ref(0)
let timer

onMounted(() => {
  timer = setInterval(() => {
    index.value = (index.value + 1) % words.length
  }, 2200)
})

onUnmounted(() => clearInterval(timer))
</script>

<template>
  <span class="bubble b1"></span>
  <span class="bubble b2"></span>
  <span class="bubble b3"></span>
  <div class="hero">
  <h1>SRUTHY DENNY</h1>
  <p :key="index">{{ words[index] }}</p>
  </div>
</template>

<style scoped>

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

@keyframes float {
  0%,
  100% {
    transform: translate(0, 0);
  }
  50% {
    transform: translate(10px, -16px);
  }
}


.hero {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 70vh;
  text-align: center;
  position: relative;
}

 .hero h1 {
  font-family: 'Montserrat', sans-serif;
  font-weight: 800;
  font-size: clamp(2.5rem, 7vw, 5.2rem);
  animation: fade-up 1s ease both;
  position: relative;
  z-index: 1;
}

.hero p {
  font-family: 'Montserrat', sans-serif;
  font-weight: 300;
  font-size: clamp(1.2rem, 3vw, 2.5rem);
  animation: fade-up 1s ease 0.5s both;
  position: relative;
  z-index: 1;
}

.bubble {
  position: absolute;
  border-radius: 50%;
  background: rgba(181, 101, 95, 0.22);
  animation: float 5s ease-in-out infinite;
}

.b1 { width: 120px; height: 120px; left: 15%; top: 20%; }
.b2 { width: 70px; height: 70px; right: 18%; top: 15%; animation-duration: 4s; animation-delay: -1s; }
.b3 { width: 90px; height: 90px; right: 25%; bottom: 20%; animation-duration: 6s; animation-delay: -2s; }

</style>