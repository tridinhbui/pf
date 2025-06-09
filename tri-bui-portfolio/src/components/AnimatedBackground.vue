<template>
  <div class="animated-background">
    <!-- Enhanced Galaxy Stars Layer -->
    <div class="galaxy-stars-layer">
      <div 
        class="galaxy-star" 
        v-for="star in galaxyStars" 
        :key="star.id"
        :style="star.style"
        :class="star.class"
      ></div>
    </div>

    <!-- Cosmic Particles Layer -->
    <div class="cosmic-particles-layer">
      <div 
        class="cosmic-particle" 
        v-for="particle in cosmicParticles" 
        :key="particle.id"
        :style="particle.style"
        :class="particle.class"
      ></div>
    </div>

    <!-- Planetary System -->
    <div class="planetary-system">
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
        <div class="planet-aurora" v-if="planet.hasAurora"></div>
      </div>
    </div>

    <!-- Orbital Paths -->
    <div class="orbital-paths-layer">
      <div 
        class="orbital-path" 
        v-for="orbit in orbitalPaths" 
        :key="orbit.id"
        :style="orbit.style"
      >
        <div class="orbiting-star" v-for="n in orbit.stars" :key="n"></div>
      </div>
    </div>

    <!-- Galaxy Nebula -->
    <div class="galaxy-nebula-layer">
      <div 
        class="nebula" 
        v-for="nebula in nebulas" 
        :key="nebula.id"
        :style="nebula.style"
        :class="nebula.class"
      ></div>
    </div>

    <!-- Cosmic Grid -->
    <div class="cosmic-grid-layer">
      <div class="cosmic-grid"></div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'

// Galaxy Stars - Further reduced quantity
const galaxyStars = computed(() => {
  const stars = []
  for (let i = 0; i < 20; i++) {
    const size = Math.random() * 3 + 1
    const twinkleSpeed = Math.random() * 3 + 2
    const opacity = Math.random() * 0.8 + 0.2
    
    stars.push({
      id: `star-${i}`,
      style: {
        left: `${Math.random() * 100}%`,
        top: `${Math.random() * 100}%`,
        width: `${size}px`,
        height: `${size}px`,
        animationDuration: `${twinkleSpeed}s`,
        animationDelay: `${Math.random() * 5}s`,
        opacity: opacity
      },
      class: getStarClass(i)
    })
  }
  return stars
})

// Cosmic Particles - Further reduced quantity
const cosmicParticles = computed(() => {
  const particles = []
  for (let i = 0; i < 10; i++) {
    const size = Math.random() * 2 + 0.5
    const speed = Math.random() * 20 + 10
    const direction = Math.random() * 360
    
    particles.push({
      id: `particle-${i}`,
      style: {
        left: `${Math.random() * 100}%`,
        top: `${Math.random() * 100}%`,
        width: `${size}px`,
        height: `${size}px`,
        animationDuration: `${speed}s`,
        animationDelay: `${Math.random() * 10}s`,
        '--direction': `${direction}deg`
      },
      class: getParticleClass(i)
    })
  }
  return particles
})

// Planets - Further reduced quantity
const planets = computed(() => {
  const planetData = []
  for (let i = 0; i < 2; i++) {
    const size = Math.random() * 60 + 30
    const orbitSpeed = Math.random() * 30 + 20
    
    planetData.push({
      id: `planet-${i}`,
      style: {
        left: `${Math.random() * 90 + 5}%`,
        top: `${Math.random() * 90 + 5}%`,
        width: `${size}px`,
        height: `${size}px`,
        animationDuration: `${orbitSpeed}s`,
        animationDelay: `${Math.random() * 10}s`
      },
      class: getPlanetClass(i),
      hasRing: Math.random() > 0.7,
      hasMoon: Math.random() > 0.6,
      hasAurora: Math.random() > 0.8
    })
  }
  return planetData
})

// Orbital Paths - Reduced quantity
const orbitalPaths = computed(() => {
  const paths = []
  for (let i = 0; i < 3; i++) {
    const size = Math.random() * 300 + 200
    const rotationSpeed = Math.random() * 40 + 30
    
    paths.push({
      id: `orbit-${i}`,
      style: {
        left: `${Math.random() * 70 + 15}%`,
        top: `${Math.random() * 70 + 15}%`,
        width: `${size}px`,
        height: `${size}px`,
        animationDuration: `${rotationSpeed}s`,
        animationDelay: `${Math.random() * 15}s`
      },
      stars: Math.floor(Math.random() * 3) + 1
    })
  }
  return paths
})

// Nebulas - Reduced quantity
const nebulas = computed(() => {
  const nebulaData = []
  for (let i = 0; i < 2; i++) {
    const width = Math.random() * 400 + 200
    const height = Math.random() * 300 + 150
    const driftSpeed = Math.random() * 50 + 40
    
    nebulaData.push({
      id: `nebula-${i}`,
      style: {
        left: `${Math.random() * 80 + 10}%`,
        top: `${Math.random() * 80 + 10}%`,
        width: `${width}px`,
        height: `${height}px`,
        animationDuration: `${driftSpeed}s`,
        animationDelay: `${Math.random() * 20}s`
      },
      class: getNebulaClass(i)
    })
  }
  return nebulaData
})

// Helper functions for classes
const getStarClass = (index: number) => {
  const classes = ['normal-star', 'pulse-star', 'bright-star', 'dim-star']
  return classes[index % classes.length]
}

const getParticleClass = (index: number) => {
  const classes = ['drift-particle', 'spiral-particle', 'bounce-particle', 'flow-particle']
  return classes[index % classes.length]
}

const getPlanetClass = (index: number) => {
  const classes = ['gas-giant', 'rocky-planet', 'ice-planet', 'lava-planet']
  return classes[index % classes.length]
}

const getNebulaClass = (index: number) => {
  const classes = ['purple-nebula', 'blue-nebula', 'green-nebula', 'red-nebula']
  return classes[index % classes.length]
}
</script>

<style scoped>
.animated-background {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
  pointer-events: none;
  background: #ffffff;
  overflow: hidden;
  opacity: 0.6;
}

/* ===== ENHANCED GALAXY STARS ===== */
.galaxy-stars-layer {
  position: absolute;
  width: 100%;
  height: 100%;
}

.galaxy-star {
  position: absolute;
  background: #000000;
  border-radius: 50%;
  box-shadow: none;
}

.normal-star {
  animation: star-twinkle infinite ease-in-out;
}

.pulse-star {
  animation: star-pulse infinite ease-in-out;
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.4);
}

.bright-star {
  animation: star-bright infinite ease-in-out;
  box-shadow: 0 0 12px rgba(0, 0, 0, 0.5);
}

.dim-star {
  animation: star-dim infinite ease-in-out;
  opacity: 0.2;
}

@keyframes star-twinkle {
  0%, 100% { opacity: 0.3; transform: scale(1); }
  50% { opacity: 1; transform: scale(1.2); }
}

@keyframes star-pulse {
  0%, 100% { opacity: 0.5; transform: scale(1); box-shadow: 0 0 8px rgba(0, 0, 0, 0.4); }
  50% { opacity: 1; transform: scale(2); box-shadow: 0 0 20px rgba(0, 0, 0, 0.6); }
}

@keyframes star-bright {
  0%, 100% { opacity: 0.8; transform: scale(1) rotate(0deg); }
  50% { opacity: 1; transform: scale(1.5) rotate(180deg); }
}

@keyframes star-dim {
  0%, 100% { opacity: 0.2; }
  50% { opacity: 0.6; }
}

/* ===== COSMIC PARTICLES ===== */
.cosmic-particles-layer {
  position: absolute;
  width: 100%;
  height: 100%;
}

.cosmic-particle {
  position: absolute;
  background: radial-gradient(circle, rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.1));
  border-radius: 50%;
}

.drift-particle {
  animation: particle-drift infinite linear;
}

.spiral-particle {
  animation: particle-spiral infinite linear;
}

.bounce-particle {
  animation: particle-bounce infinite ease-in-out;
}

.flow-particle {
  animation: particle-flow infinite linear;
}

@keyframes particle-drift {
  0% { transform: translateX(0) translateY(0) scale(0.5); opacity: 0; }
  10% { opacity: 1; }
  90% { opacity: 1; }
  100% { transform: translateX(100vw) translateY(-50px) scale(1.5); opacity: 0; }
}

@keyframes particle-spiral {
  0% { 
    transform: translateX(0) translateY(0) scale(0.5) rotate(0deg); 
    opacity: 0; 
  }
  10% { opacity: 1; }
  90% { opacity: 1; }
  100% { 
    transform: translateX(50px) translateY(-100px) scale(2) rotate(720deg); 
    opacity: 0; 
  }
}

@keyframes particle-bounce {
  0%, 100% { transform: translateY(0) scale(1); }
  25% { transform: translateY(-30px) scale(1.2); }
  50% { transform: translateY(-60px) scale(1.5); }
  75% { transform: translateY(-30px) scale(1.2); }
}

@keyframes particle-flow {
  0% { 
    transform: translateX(-50px) translateY(100vh) scale(0); 
    opacity: 0; 
  }
  5% { opacity: 1; transform: scale(1); }
  95% { opacity: 1; }
  100% { 
    transform: translateX(50px) translateY(-50px) scale(2); 
    opacity: 0; 
  }
}

/* ===== PLANETARY SYSTEM ===== */
.planetary-system {
  position: absolute;
  width: 100%;
  height: 100%;
}

.cosmic-planet {
  position: absolute;
  border-radius: 50%;
  animation: planet-orbit infinite linear;
}

.gas-giant,
.rocky-planet,
.ice-planet,
.lava-planet {
  background: #000000;
  box-shadow: none;
  border: 1px solid #cccccc;
}

.planet-core {
  position: absolute;
  top: 20%;
  left: 20%;
  width: 60%;
  height: 60%;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.3), transparent);
  border-radius: 50%;
  animation: core-glow 4s ease-in-out infinite;
}

.planet-ring {
  position: absolute;
  top: -15%;
  left: -15%;
  width: 130%;
  height: 130%;
  border: 2px solid rgba(0, 0, 0, 0.3);
  border-radius: 50%;
  animation: ring-rotate 20s linear infinite;
}

.planet-moon {
  position: absolute;
  width: 20%;
  height: 20%;
  background: radial-gradient(circle, #888888, #444444);
  border-radius: 50%;
  top: -10%;
  left: 50%;
  animation: moon-orbit 15s linear infinite;
}

.planet-aurora {
  position: absolute;
  top: -20%;
  left: -20%;
  width: 140%;
  height: 140%;
  background: conic-gradient(from 0deg, transparent, rgba(0, 0, 0, 0.1), transparent, rgba(0, 0, 0, 0.1), transparent);
  border-radius: 50%;
  animation: aurora-dance 8s ease-in-out infinite;
}

@keyframes planet-orbit {
  0% { transform: rotate(0deg) translateX(50px) rotate(0deg); }
  100% { transform: rotate(360deg) translateX(50px) rotate(-360deg); }
}

@keyframes lava-pulse {
  0%, 100% { box-shadow: 0 0 35px rgba(0, 0, 0, 0.4); }
  50% { box-shadow: 0 0 50px rgba(0, 0, 0, 0.6), 0 0 70px rgba(0, 0, 0, 0.3); }
}

@keyframes core-glow {
  0%, 100% { opacity: 0.3; transform: scale(1); }
  50% { opacity: 0.6; transform: scale(1.1); }
}

@keyframes ring-rotate {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

@keyframes moon-orbit {
  0% { transform: rotate(0deg) translateY(-80px) rotate(0deg); }
  100% { transform: rotate(360deg) translateY(-80px) rotate(-360deg); }
}

@keyframes aurora-dance {
  0%, 100% { opacity: 0.3; transform: rotate(0deg); }
  50% { opacity: 0.7; transform: rotate(180deg); }
}

/* ===== ORBITAL PATHS ===== */
.orbital-paths-layer {
  position: absolute;
  width: 100%;
  height: 100%;
}

.orbital-path {
  position: absolute;
  border: 1px solid rgba(0, 0, 0, 0.1);
  border-radius: 50%;
  animation: orbital-rotation infinite linear;
}

.orbiting-star {
  position: absolute;
  width: 4px;
  height: 4px;
  background: radial-gradient(circle, #000000, rgba(0, 0, 0, 0.6));
  border-radius: 50%;
  top: 0;
  left: 50%;
  margin-left: -2px;
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.3);
  animation: star-orbit 10s linear infinite;
}

.orbiting-star:nth-child(2) {
  animation-delay: -3.33s;
  top: 66.67%;
  left: 0;
  margin-left: 0;
  margin-top: -2px;
}

.orbiting-star:nth-child(3) {
  animation-delay: -6.67s;
  top: 33.33%;
  left: 100%;
  margin-left: -4px;
  margin-top: -2px;
}

@keyframes orbital-rotation {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

@keyframes star-orbit {
  0% { transform: rotate(0deg) translateY(-50%) rotate(0deg); }
  100% { transform: rotate(360deg) translateY(-50%) rotate(-360deg); }
}

/* ===== GALAXY NEBULA ===== */
.galaxy-nebula-layer {
  position: absolute;
  width: 100%;
  height: 100%;
}

.nebula {
  position: absolute;
  border-radius: 50%;
  filter: blur(3px);
  animation: nebula-drift infinite ease-in-out;
}

.purple-nebula,
.blue-nebula,
.green-nebula,
.red-nebula {
  background: rgba(0, 0, 0, 0.05);
  border-radius: 50%;
}

@keyframes nebula-drift {
  0%, 100% { transform: translateX(0) translateY(0) rotate(0deg); opacity: 0.3; }
  33% { transform: translateX(50px) translateY(-30px) rotate(120deg); opacity: 0.6; }
  66% { transform: translateX(-30px) translateY(50px) rotate(240deg); opacity: 0.4; }
}

/* ===== COSMIC GRID ===== */
.cosmic-grid-layer {
  position: absolute;
  width: 100%;
  height: 100%;
  opacity: 0.1;
}

.cosmic-grid {
  width: 100%;
  height: 100%;
  background-image: 
    linear-gradient(rgba(0, 0, 0, 0.1) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0, 0, 0, 0.1) 1px, transparent 1px);
  background-size: 50px 50px;
  animation: grid-pulse 30s ease-in-out infinite;
}

@keyframes grid-pulse {
  0%, 100% { opacity: 0.1; transform: scale(1); }
  50% { opacity: 0.3; transform: scale(1.02); }
}

/* Responsive */
@media (max-width: 768px) {
  .cosmic-particle {
    width: 1px !important;
    height: 1px !important;
  }
  
  .cosmic-planet {
    width: 20px !important;
    height: 20px !important;
  }
  
  .orbital-path {
    width: 150px !important;
    height: 150px !important;
  }
  
  .nebula {
    width: 200px !important;
    height: 150px !important;
  }
}

/* Reduce motion for accessibility */
@media (prefers-reduced-motion: reduce) {
  .galaxy-star, .cosmic-particle, .cosmic-planet, .orbital-path, .nebula, .cosmic-grid {
    animation: none !important;
    opacity: 0.3 !important;
  }
}
</style> 