<template>
  <div class="animated-background">
    <!-- Enhanced Stars Layer -->
    <div class="stars-layer">
      <div 
        class="star" 
        v-for="star in stars" 
        :key="star.id"
        :style="star.style"
        :class="star.class"
      ></div>
    </div>

    <!-- Planetary System -->
    <div class="planets-layer">
      <div 
        class="cosmic-planet" 
        v-for="planet in planets" 
        :key="planet.id"
        :style="planet.style"
        :class="planet.class"
      >
        <div class="planet-core"></div>
        <div class="planet-ring" v-if="planet.hasRing"></div>
        <div class="planet-moon" v-if="planet.hasMoon"></div>
      </div>
    </div>

    <!-- Simple Orbital Paths -->
    <div class="orbits-layer">
      <div 
        class="orbital-path" 
        v-for="orbit in orbits" 
        :key="orbit.id"
        :style="orbit.style"
      >
        <div class="orbiting-star"></div>
      </div>
    </div>

    <!-- Subtle Grid Pattern -->
    <div class="space-grid"></div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

interface AnimatedElement {
  id: number;
  style: Record<string, string>;
  class?: string;
  hasRing?: boolean;
  hasMoon?: boolean;
}

const stars = ref<AnimatedElement[]>([])
const planets = ref<AnimatedElement[]>([])
const orbits = ref<AnimatedElement[]>([])

const generateStars = () => {
  for (let i = 0; i < 100; i++) {
    const starType = Math.random() > 0.6 ? 'star-twinkle' : 'star-normal'
    stars.value.push({
      id: i,
      class: starType,
      style: {
        left: `${Math.random() * 100}%`,
        top: `${Math.random() * 100}%`,
        animationDelay: `${Math.random() * 8}s`,
        animationDuration: `${3 + Math.random() * 5}s`,
        '--star-size': `${1 + Math.random() * 2}px`
      }
    })
  }
}

const generatePlanets = () => {
  for (let i = 0; i < 8; i++) {
    const hasRing = Math.random() > 0.7
    const hasMoon = Math.random() > 0.6
    
    planets.value.push({
      id: i,
      class: `planet-${Math.floor(Math.random() * 3) + 1}`,
      hasRing,
      hasMoon,
      style: {
        left: `${Math.random() * 100}%`,
        top: `${Math.random() * 100}%`,
        animationDelay: `${Math.random() * 20}s`,
        animationDuration: `${15 + Math.random() * 25}s`,
        '--planet-size': `${30 + Math.random() * 60}px`
      }
    })
  }
}

const generateOrbits = () => {
  for (let i = 0; i < 12; i++) {
    orbits.value.push({
      id: i,
      style: {
        left: `${Math.random() * 100}%`,
        top: `${Math.random() * 100}%`,
        animationDelay: `${Math.random() * 30}s`,
        animationDuration: `${20 + Math.random() * 40}s`,
        '--orbit-size': `${80 + Math.random() * 150}px`
      }
    })
  }
}

onMounted(() => {
  generateStars()
  generatePlanets()
  generateOrbits()
})
</script>

<style scoped>
.animated-background {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
  overflow: hidden;
  pointer-events: none;
}

/* Stars Layer */
.stars-layer {
  position: absolute;
  width: 100%;
  height: 100%;
}

.star {
  position: absolute;
  background: #ffffff;
  border-radius: 50%;
  width: var(--star-size, 2px);
  height: var(--star-size, 2px);
  box-shadow: 0 0 6px #ffffff;
}

.star-normal {
  animation: star-glow 4s ease-in-out infinite;
}

.star-twinkle {
  animation: star-twinkle 3s ease-in-out infinite;
}

@keyframes star-glow {
  0%, 100% { 
    opacity: 0.6; 
    transform: scale(1);
    box-shadow: 0 0 6px #ffffff;
  }
  50% { 
    opacity: 1; 
    transform: scale(1.2);
    box-shadow: 0 0 12px #ffffff;
  }
}

@keyframes star-twinkle {
  0%, 100% { opacity: 0.3; }
  25% { opacity: 1; }
  50% { opacity: 0.5; }
  75% { opacity: 0.9; }
}

/* Planets Layer */
.planets-layer {
  position: absolute;
  width: 100%;
  height: 100%;
}

.cosmic-planet {
  position: absolute;
  width: var(--planet-size, 40px);
  height: var(--planet-size, 40px);
  animation: planet-float 20s ease-in-out infinite;
}

.planet-core {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  background: radial-gradient(circle at 30% 30%, #ffffff, #888888, #333333);
  box-shadow: 0 0 20px rgba(255, 255, 255, 0.3);
}

.planet-1 .planet-core {
  background: radial-gradient(circle at 30% 30%, #ffffff, #cccccc, #666666);
}

.planet-2 .planet-core {
  background: radial-gradient(circle at 30% 30%, #ffffff, #aaaaaa, #444444);
}

.planet-3 .planet-core {
  background: radial-gradient(circle at 30% 30%, #ffffff, #999999, #222222);
}

.planet-ring {
  position: absolute;
  top: -20%;
  left: -20%;
  right: -20%;
  bottom: -20%;
  border: 2px solid rgba(255, 255, 255, 0.3);
  border-radius: 50%;
  animation: ring-rotate 10s linear infinite;
}

.planet-moon {
  position: absolute;
  width: 25%;
  height: 25%;
  background: #cccccc;
  border-radius: 50%;
  top: -15%;
  left: 50%;
  margin-left: -12.5%;
  animation: moon-orbit 8s linear infinite;
  box-shadow: 0 0 8px rgba(255, 255, 255, 0.5);
}

@keyframes planet-float {
  0%, 100% { 
    transform: translateY(0) rotate(0deg); 
    opacity: 0.8;
  }
  25% { 
    transform: translateY(-30px) rotate(90deg); 
    opacity: 1;
  }
  50% { 
    transform: translateY(-15px) rotate(180deg); 
    opacity: 0.9;
  }
  75% { 
    transform: translateY(-40px) rotate(270deg); 
    opacity: 1;
  }
}

@keyframes ring-rotate {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

@keyframes moon-orbit {
  0% { 
    transform: rotate(0deg) translateY(-50px) rotate(0deg);
    opacity: 0.8;
  }
  100% { 
    transform: rotate(360deg) translateY(-50px) rotate(-360deg);
    opacity: 0.8;
  }
}

/* Orbital Paths */
.orbits-layer {
  position: absolute;
  width: 100%;
  height: 100%;
}

.orbital-path {
  position: absolute;
  width: var(--orbit-size, 100px);
  height: var(--orbit-size, 100px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 50%;
  animation: orbit-rotate 30s linear infinite;
}

.orbiting-star {
  position: absolute;
  width: 4px;
  height: 4px;
  background: #ffffff;
  border-radius: 50%;
  top: 0;
  left: 50%;
  margin-left: -2px;
  animation: star-orbit 15s linear infinite;
  box-shadow: 0 0 8px #ffffff;
}

@keyframes orbit-rotate {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

@keyframes star-orbit {
  0% { 
    transform: rotate(0deg) translateY(calc(var(--orbit-size, 100px) / -2)) rotate(0deg);
    opacity: 0.6;
  }
  50% {
    opacity: 1;
  }
  100% { 
    transform: rotate(360deg) translateY(calc(var(--orbit-size, 100px) / -2)) rotate(-360deg);
    opacity: 0.6;
  }
}

/* Space Grid */
.space-grid {
  position: absolute;
  width: 100%;
  height: 100%;
  background-image: 
    linear-gradient(rgba(255, 255, 255, 0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 255, 255, 0.03) 1px, transparent 1px);
  background-size: 50px 50px;
  animation: grid-drift 60s linear infinite;
  opacity: 0.5;
}

@keyframes grid-drift {
  0% { transform: translate(0, 0); }
  100% { transform: translate(50px, 50px); }
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .cosmic-planet {
    --planet-size: 25px !important;
  }
  
  .orbital-path {
    --orbit-size: 60px !important;
  }
  
  .space-grid {
    background-size: 30px 30px;
  }
}

/* Reduced motion */
@media (prefers-reduced-motion: reduce) {
  .star, .cosmic-planet, .orbital-path, .space-grid {
    animation: none !important;
  }
}
</style> 