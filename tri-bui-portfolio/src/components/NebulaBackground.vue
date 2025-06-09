<template>
  <div class="nebula-background">
    <div class="nebula-layer nebula-primary"></div>
    <div class="nebula-layer nebula-secondary"></div>
    <div class="nebula-layer nebula-accent"></div>
  </div>
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue'

const nebulaRef = ref<HTMLElement>()

onMounted(() => {
  // Add subtle animation to nebula layers
  const layers = document.querySelectorAll('.nebula-layer')
  
  layers.forEach((layer, index) => {
    const element = layer as HTMLElement
    
    // Create floating animation with different speeds
    const animationDuration = 20 + (index * 10) // 20s, 30s, 40s
    const direction = index % 2 === 0 ? 1 : -1
    
    element.style.animation = `float-nebula ${animationDuration}s ease-in-out infinite`
    element.style.animationDelay = `${index * 5}s`
    
    if (direction === -1) {
      element.style.animationDirection = 'reverse'
    }
  })
})
</script>

<style scoped>
.nebula-background {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  z-index: -2;
  pointer-events: none;
  overflow: hidden;
}

.nebula-layer {
  position: absolute;
  width: 120%;
  height: 120%;
  border-radius: 50%;
  filter: blur(120px);
  opacity: 0.6;
  top: -10%;
  left: -10%;
}

.nebula-primary {
  background: radial-gradient(
    circle at 30% 30%, 
    rgba(158, 75, 255, 0.3) 0%, 
    transparent 70%
  );
  transform: scale(1.2);
}

.nebula-secondary {
  background: radial-gradient(
    circle at 70% 60%, 
    rgba(0, 230, 255, 0.2) 0%, 
    transparent 60%
  );
  transform: scale(0.8);
}

.nebula-accent {
  background: radial-gradient(
    circle at 50% 80%, 
    rgba(73, 255, 206, 0.15) 0%, 
    transparent 50%
  );
  transform: scale(1.5);
}

@keyframes float-nebula {
  0%, 100% {
    transform: translate(0, 0) rotate(0deg) scale(var(--scale, 1));
  }
  25% {
    transform: translate(20px, -30px) rotate(90deg) scale(calc(var(--scale, 1) * 1.1));
  }
  50% {
    transform: translate(-15px, 25px) rotate(180deg) scale(var(--scale, 1));
  }
  75% {
    transform: translate(-25px, -20px) rotate(270deg) scale(calc(var(--scale, 1) * 0.9));
  }
}

.nebula-primary {
  --scale: 1.2;
}

.nebula-secondary {
  --scale: 0.8;
}

.nebula-accent {
  --scale: 1.5;
}

/* Reduce motion for accessibility */
@media (prefers-reduced-motion: reduce) {
  .nebula-layer {
    animation: none !important;
  }
}

/* Hide on very small screens for performance */
@media (max-width: 480px) {
  .nebula-background {
    display: none;
  }
}
</style> 