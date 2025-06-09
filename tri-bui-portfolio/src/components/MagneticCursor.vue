<template>
  <div class="magnetic-cursor" ref="cursorRef">
    <div class="cursor-dot" ref="dotRef"></div>
    <div class="cursor-ring" ref="ringRef"></div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'
import { gsap } from 'gsap'

const cursorRef = ref<HTMLElement>()
const dotRef = ref<HTMLElement>()
const ringRef = ref<HTMLElement>()

let mouseX = 0
let mouseY = 0
let cursorX = 0
let cursorY = 0
let isHovering = false

onMounted(() => {
  if (!cursorRef.value || !dotRef.value || !ringRef.value) return

  // Mouse move handler
  const handleMouseMove = (e: MouseEvent) => {
    mouseX = e.clientX
    mouseY = e.clientY
  }

  // Cursor animation loop
  const animateCursor = () => {
    const speed = isHovering ? 0.2 : 0.1
    
    cursorX += (mouseX - cursorX) * speed
    cursorY += (mouseY - cursorY) * speed

    if (dotRef.value) {
      gsap.set(dotRef.value, {
        x: cursorX,
        y: cursorY,
      })
    }

    if (ringRef.value) {
      gsap.set(ringRef.value, {
        x: cursorX,
        y: cursorY,
      })
    }

    requestAnimationFrame(animateCursor)
  }

  // Magnetic effect for interactive elements
  const handleMouseEnter = (e: Event) => {
    const target = e.target as HTMLElement
    
    if (target.classList.contains('magnetic-target')) {
      isHovering = true
      
      if (dotRef.value) {
        gsap.to(dotRef.value, {
          scale: 0.5,
          duration: 0.3,
          ease: "power2.out"
        })
      }
      
      if (ringRef.value) {
        gsap.to(ringRef.value, {
          scale: 1.5,
          borderColor: 'var(--color-primary)',
          duration: 0.3,
          ease: "power2.out"
        })
      }

      // Magnetic attraction
      const rect = target.getBoundingClientRect()
      const centerX = rect.left + rect.width / 2
      const centerY = rect.top + rect.height / 2
      
      if (cursorRef.value) {
        gsap.to(cursorRef.value, {
          x: centerX - mouseX,
          y: centerY - mouseY,
          duration: 0.3,
          ease: "power2.out"
        })
      }
    }
  }

  const handleMouseLeave = () => {
    isHovering = false
    
    if (dotRef.value) {
      gsap.to(dotRef.value, {
        scale: 1,
        duration: 0.3,
        ease: "power2.out"
      })
    }
    
    if (ringRef.value) {
      gsap.to(ringRef.value, {
        scale: 1,
        borderColor: 'var(--color-gray-400)',
        duration: 0.3,
        ease: "power2.out"
      })
    }

    if (cursorRef.value) {
      gsap.to(cursorRef.value, {
        x: 0,
        y: 0,
        duration: 0.3,
        ease: "power2.out"
      })
    }
  }

  // Event listeners
  document.addEventListener('mousemove', handleMouseMove)
  document.querySelectorAll('.magnetic-target').forEach(el => {
    el.addEventListener('mouseenter', handleMouseEnter)
    el.addEventListener('mouseleave', handleMouseLeave)
  })

  // Start animation
  animateCursor()

  // Cleanup
  onUnmounted(() => {
    document.removeEventListener('mousemove', handleMouseMove)
    document.querySelectorAll('.magnetic-target').forEach(el => {
      el.removeEventListener('mouseenter', handleMouseEnter)
      el.removeEventListener('mouseleave', handleMouseLeave)
    })
  })
})
</script>

<style scoped>
.magnetic-cursor {
  position: fixed;
  top: 0;
  left: 0;
  pointer-events: none;
  z-index: 9999;
  mix-blend-mode: difference;
}

.cursor-dot {
  position: absolute;
  width: 8px;
  height: 8px;
  background: var(--gradient-galaxy);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  box-shadow: 
    0 0 15px var(--color-primary-glow),
    0 0 30px rgba(158, 75, 255, 0.3),
    0 0 45px rgba(73, 255, 206, 0.2);
  animation: cosmic-pulse 2s ease-in-out infinite;
}

.cursor-ring {
  position: absolute;
  width: 40px;
  height: 40px;
  border: 2px solid transparent;
  border-radius: 50%;
  transform: translate(-50%, -50%);
  background: linear-gradient(45deg, var(--color-primary), var(--color-secondary), var(--color-accent)) padding-box,
              linear-gradient(45deg, var(--color-primary), var(--color-secondary), var(--color-accent)) border-box;
  opacity: 0.6;
  animation: cosmic-orbit 4s linear infinite;
}

@keyframes cosmic-pulse {
  0%, 100% {
    transform: translate(-50%, -50%) scale(1);
    box-shadow: 
      0 0 15px var(--color-primary-glow),
      0 0 30px rgba(158, 75, 255, 0.3),
      0 0 45px rgba(73, 255, 206, 0.2);
  }
  50% {
    transform: translate(-50%, -50%) scale(1.2);
    box-shadow: 
      0 0 25px var(--color-primary-glow),
      0 0 50px rgba(158, 75, 255, 0.5),
      0 0 75px rgba(73, 255, 206, 0.3);
  }
}

@keyframes cosmic-orbit {
  0% {
    transform: translate(-50%, -50%) rotate(0deg);
  }
  100% {
    transform: translate(-50%, -50%) rotate(360deg);
  }
}

/* Hide cursor on touch devices */
@media (hover: none) {
  .magnetic-cursor {
    display: none;
  }
}
</style> 