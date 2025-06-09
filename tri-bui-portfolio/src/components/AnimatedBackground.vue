<template>
  <div class="animated-background">
    <!-- Stars Layer -->
    <div class="stars-layer">
      <div 
        class="star" 
        v-for="star in stars" 
        :key="star.id"
        :style="star.style"
      ></div>
    </div>

    <!-- Atomic Particles Layer -->
    <div class="particles-layer">
      <div 
        class="particle" 
        v-for="particle in particles" 
        :key="particle.id"
        :style="particle.style"
      ></div>
    </div>

    <!-- Floating Orbs -->
    <div class="orbs-layer">
      <div 
        class="orb" 
        v-for="orb in orbs" 
        :key="orb.id"
        :style="orb.style"
      ></div>
    </div>

    <!-- Grid Pattern -->
    <div class="grid-pattern"></div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

interface AnimatedElement {
  id: number;
  style: Record<string, string>;
}

const stars = ref<AnimatedElement[]>([])
const particles = ref<AnimatedElement[]>([])
const orbs = ref<AnimatedElement[]>([])

const generateStars = () => {
  for (let i = 0; i < 100; i++) {
    stars.value.push({
      id: i,
      style: {
        left: `${Math.random() * 100}%`,
        top: `${Math.random() * 100}%`,
        animationDelay: `${Math.random() * 5}s`,
        animationDuration: `${2 + Math.random() * 3}s`,
        '--star-size': `${1 + Math.random() * 3}px`
      }
    })
  }
}

const generateParticles = () => {
  for (let i = 0; i < 50; i++) {
    particles.value.push({
      id: i,
      style: {
        left: `${Math.random() * 100}%`,
        top: `${Math.random() * 100}%`,
        animationDelay: `${Math.random() * 10}s`,
        animationDuration: `${5 + Math.random() * 10}s`,
        '--particle-size': `${2 + Math.random() * 4}px`
      }
    })
  }
}

const generateOrbs = () => {
  for (let i = 0; i < 8; i++) {
    orbs.value.push({
      id: i,
      style: {
        left: `${Math.random() * 100}%`,
        top: `${Math.random() * 100}%`,
        animationDelay: `${Math.random() * 8}s`,
        animationDuration: `${8 + Math.random() * 12}s`,
        '--orb-size': `${20 + Math.random() * 40}px`,
        '--orb-opacity': `${0.02 + Math.random() * 0.08}`
      }
    })
  }
}

onMounted(() => {
  generateStars()
  generateParticles()
  generateOrbs()
})
</script>

<style scoped>
.animated-background {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  overflow: hidden;
  pointer-events: none;
}

/* Stars Animation */
.stars-layer {
  position: absolute;
  width: 100%;
  height: 100%;
}

.star {
  position: absolute;
  width: var(--star-size);
  height: var(--star-size);
  background: #000000;
  border-radius: 50%;
  opacity: 0;
  animation: twinkle infinite ease-in-out;
}

@keyframes twinkle {
  0%, 100% { 
    opacity: 0; 
    transform: scale(1);
  }
  50% { 
    opacity: 0.8; 
    transform: scale(1.2);
  }
}

/* Particles Animation */
.particles-layer {
  position: absolute;
  width: 100%;
  height: 100%;
}

.particle {
  position: absolute;
  width: var(--particle-size);
  height: var(--particle-size);
  background: radial-gradient(circle, #333333 0%, transparent 70%);
  border-radius: 50%;
  opacity: 0.4;
  animation: float infinite linear;
}

@keyframes float {
  0% {
    transform: translateY(100vh) translateX(0) rotate(0deg);
    opacity: 0;
  }
  10% {
    opacity: 0.4;
  }
  90% {
    opacity: 0.4;
  }
  100% {
    transform: translateY(-100px) translateX(100px) rotate(360deg);
    opacity: 0;
  }
}

/* Orbs Animation */
.orbs-layer {
  position: absolute;
  width: 100%;
  height: 100%;
}

.orb {
  position: absolute;
  width: var(--orb-size);
  height: var(--orb-size);
  background: radial-gradient(circle, rgba(0, 0, 0, var(--orb-opacity)) 0%, transparent 70%);
  border-radius: 50%;
  animation: drift infinite ease-in-out;
}

@keyframes drift {
  0%, 100% {
    transform: translate(0, 0) scale(1);
  }
  25% {
    transform: translate(20px, -30px) scale(1.1);
  }
  50% {
    transform: translate(-15px, -60px) scale(0.9);
  }
  75% {
    transform: translate(-30px, -30px) scale(1.05);
  }
}

/* Grid Pattern */
.grid-pattern {
  position: absolute;
  width: 100%;
  height: 100%;
  background-image: 
    linear-gradient(rgba(0, 0, 0, 0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0, 0, 0, 0.03) 1px, transparent 1px);
  background-size: 50px 50px;
  animation: grid-move 20s linear infinite;
}

@keyframes grid-move {
  0% {
    transform: translate(0, 0);
  }
  100% {
    transform: translate(50px, 50px);
  }
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .star {
    --star-size: 1px !important;
  }
  
  .particle {
    --particle-size: 2px !important;
  }
  
  .orb {
    --orb-size: 20px !important;
  }
}

/* Reduce motion for accessibility */
@media (prefers-reduced-motion: reduce) {
  .star,
  .particle,
  .orb,
  .grid-pattern {
    animation: none !important;
  }
}
</style> 