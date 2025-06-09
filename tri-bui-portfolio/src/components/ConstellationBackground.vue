<template>
  <div class="constellation-background">
    <!-- Floating Neural Networks -->
    <div 
      v-for="star in stars" 
      :key="star.id"
      class="floating-star"
      :style="{
        left: star.x + '%',
        top: star.y + '%',
        animationDelay: star.delay + 's',
        animationDuration: star.duration + 's'
      }"
    >
      <div 
        class="star-core"
        :class="star.type"
      ></div>
      <div class="star-glow"></div>
    </div>

    <!-- Neural Connection Lines -->
    <svg class="neural-connections" viewBox="0 0 100 100" preserveAspectRatio="none">
      <defs>
        <linearGradient id="neuralGradient" x1="0%" y1="0%" x2="100%" y2="100%">
          <stop offset="0%" style="stop-color:#FFD700;stop-opacity:0.6" />
          <stop offset="50%" style="stop-color:#4FC3F7;stop-opacity:0.4" />
          <stop offset="100%" style="stop-color:#9C27B0;stop-opacity:0.6" />
        </linearGradient>
      </defs>
      
      <path 
        v-for="connection in connections" 
        :key="connection.id"
        :d="connection.path"
        stroke="url(#neuralGradient)"
        stroke-width="0.1"
        fill="none"
        class="neural-path"
        :style="{ animationDelay: connection.delay + 's' }"
      />
    </svg>

    <!-- Cosmic Orbs -->
    <div 
      v-for="orb in cosmicOrbs" 
      :key="orb.id"
      class="cosmic-orb"
      :style="{
        left: orb.x + '%',
        top: orb.y + '%',
        animationDelay: orb.delay + 's'
      }"
    ></div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

// Generate mystical star positions
const stars = ref(
  Array.from({ length: 50 }, (_, i) => ({
    id: i,
    x: Math.random() * 100,
    y: Math.random() * 100,
    delay: Math.random() * 10,
    duration: 15 + Math.random() * 10,
    type: ['solar', 'neural', 'mystic'][Math.floor(Math.random() * 3)]
  }))
)

// Generate neural connections
const connections = ref(
  Array.from({ length: 15 }, (_, i) => {
    const start = { x: Math.random() * 100, y: Math.random() * 100 }
    const end = { x: Math.random() * 100, y: Math.random() * 100 }
    const mid1 = { x: (start.x + end.x) / 2 + (Math.random() - 0.5) * 30, y: (start.y + end.y) / 2 + (Math.random() - 0.5) * 30 }
    const mid2 = { x: (start.x + end.x) / 2 + (Math.random() - 0.5) * 30, y: (start.y + end.y) / 2 + (Math.random() - 0.5) * 30 }
    
    return {
      id: i,
      path: `M ${start.x} ${start.y} C ${mid1.x} ${mid1.y}, ${mid2.x} ${mid2.y}, ${end.x} ${end.y}`,
      delay: Math.random() * 5
    }
  })
)

// Generate cosmic orbs
const cosmicOrbs = ref(
  Array.from({ length: 8 }, (_, i) => ({
    id: i,
    x: Math.random() * 100,
    y: Math.random() * 100,
    delay: Math.random() * 8
  }))
)

onMounted(() => {
  // Optional: Add mouse interaction
  const handleMouseMove = (e: MouseEvent) => {
    const x = (e.clientX / window.innerWidth) * 100
    const y = (e.clientY / window.innerHeight) * 100
    
    // Subtle parallax effect
    document.documentElement.style.setProperty('--mouse-x', x + '%')
    document.documentElement.style.setProperty('--mouse-y', y + '%')
  }
  
  window.addEventListener('mousemove', handleMouseMove)
  
  return () => {
    window.removeEventListener('mousemove', handleMouseMove)
  }
})
</script>

<style scoped>
@reference 'tailwindcss';
.constellation-background {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  pointer-events: none;
  z-index: -1;
  overflow: hidden;
}

.floating-star {
  position: absolute;
  width: 4px;
  height: 4px;
  animation: floatStar infinite ease-in-out;
}

.star-core {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  position: relative;
}

.star-core.solar {
  background: radial-gradient(circle, #FFD700, #FFA500);
  box-shadow: 0 0 10px #FFD700;
}

.star-core.neural {
  background: radial-gradient(circle, #4FC3F7, #2196F3);
  box-shadow: 0 0 8px #4FC3F7;
}

.star-core.mystic {
  background: radial-gradient(circle, #9C27B0, #673AB7);
  box-shadow: 0 0 6px #9C27B0;
}

.star-glow {
  position: absolute;
  top: -100%;
  left: -100%;
  width: 300%;
  height: 300%;
  background: radial-gradient(circle, rgba(255, 215, 0, 0.1), transparent);
  border-radius: 50%;
  animation: starGlow 4s ease-in-out infinite alternate;
}

.neural-connections {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: 0.3;
}

.neural-path {
  animation: neuralFlow 8s linear infinite;
}

.cosmic-orb {
  position: absolute;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: radial-gradient(circle at 30% 30%, 
    rgba(255, 215, 0, 0.8), 
    rgba(255, 165, 0, 0.4), 
    transparent);
  animation: orbitalFloat 20s linear infinite;
  filter: blur(1px);
}

/* Animations */
@keyframes floatStar {
  0%, 100% { transform: translateY(0px) rotate(0deg); }
  25% { transform: translateY(-10px) rotate(90deg); }
  50% { transform: translateY(-5px) rotate(180deg); }
  75% { transform: translateY(-15px) rotate(270deg); }
}

@keyframes starGlow {
  0% { opacity: 0.2; transform: scale(1); }
  100% { opacity: 0.6; transform: scale(1.5); }
}

@keyframes neuralFlow {
  0% { stroke-dasharray: 0 10; stroke-dashoffset: 0; }
  50% { stroke-dasharray: 5 5; stroke-dashoffset: -5; }
  100% { stroke-dasharray: 0 10; stroke-dashoffset: -10; }
}

@keyframes orbitalFloat {
  0% { transform: rotate(0deg) translateX(50px) rotate(0deg); }
  100% { transform: rotate(360deg) translateX(50px) rotate(-360deg); }
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .floating-star {
    width: 2px;
    height: 2px;
  }
  
  .cosmic-orb {
    width: 12px;
    height: 12px;
  }
}
</style> 