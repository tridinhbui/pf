<template>
  <canvas 
    ref="canvasRef" 
    class="starfield-canvas"
  ></canvas>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

interface Star {
  x: number
  y: number
  z: number
  prevX: number
  prevY: number
  speed: number
  size: number
  opacity: number
  color: string
}

const canvasRef = ref<HTMLCanvasElement>()
let ctx: CanvasRenderingContext2D | null = null
let animationId: number
let stars: Star[] = []
let mouseX = 0
let mouseY = 0

const STAR_COUNT = 400
const COLORS = ['#9E4BFF', '#00E6FF', '#49FFCE', '#F8F9FA']

onMounted(() => {
  if (!canvasRef.value) return
  
  ctx = canvasRef.value.getContext('2d')
  if (!ctx) return
  
  setupCanvas()
  createStars()
  animate()
  
  window.addEventListener('resize', handleResize)
  window.addEventListener('mousemove', handleMouseMove)
})

onUnmounted(() => {
  if (animationId) {
    cancelAnimationFrame(animationId)
  }
  
  window.removeEventListener('resize', handleResize)
  window.removeEventListener('mousemove', handleMouseMove)
})

const setupCanvas = () => {
  if (!canvasRef.value || !ctx) return
  
  const canvas = canvasRef.value
  canvas.width = window.innerWidth
  canvas.height = window.innerHeight
}

const createStars = () => {
  if (!canvasRef.value) return
  
  const canvas = canvasRef.value
  stars = []
  
  for (let i = 0; i < STAR_COUNT; i++) {
    const star: Star = {
      x: Math.random() * canvas.width,
      y: Math.random() * canvas.height,
      z: Math.random() * 1000 + 1,
      prevX: 0,
      prevY: 0,
      speed: Math.random() * 2 + 0.1,
      size: Math.random() * 2 + 0.5,
      opacity: Math.random() * 0.8 + 0.2,
      color: COLORS[Math.floor(Math.random() * COLORS.length)]
    }
    
    star.prevX = star.x
    star.prevY = star.y
    stars.push(star)
  }
}

const updateStars = () => {
  if (!canvasRef.value) return
  
  const canvas = canvasRef.value
  const centerX = canvas.width / 2
  const centerY = canvas.height / 2
  
  stars.forEach(star => {
    star.prevX = star.x
    star.prevY = star.y
    
    // Move towards center with warp effect
    star.z -= star.speed
    
    if (star.z <= 0) {
      star.z = 1000
      star.x = Math.random() * canvas.width
      star.y = Math.random() * canvas.height
    }
    
    // Perspective projection
    const perspective = 1000
    const scale = perspective / (perspective + star.z)
    
    star.x = centerX + (star.x - centerX) * scale
    star.y = centerY + (star.y - centerY) * scale
    star.opacity = Math.max(0.1, 1 - star.z / 1000)
  })
}

const drawStars = () => {
  if (!ctx || !canvasRef.value) return
  
  const canvas = canvasRef.value
  const context = ctx // TypeScript safety
  
  // Clear with slight trail
  context.fillStyle = 'rgba(12, 14, 20, 0.1)'
  context.fillRect(0, 0, canvas.width, canvas.height)
  
  stars.forEach(star => {
    // Draw motion trail
    context.strokeStyle = star.color + '40'
    context.lineWidth = star.size * 0.5
    context.beginPath()
    context.moveTo(star.prevX, star.prevY)
    context.lineTo(star.x, star.y)
    context.stroke()
    
    // Draw star
    const gradient = context.createRadialGradient(
      star.x, star.y, 0,
      star.x, star.y, star.size * 2
    )
    gradient.addColorStop(0, star.color + Math.floor(star.opacity * 255).toString(16).padStart(2, '0'))
    gradient.addColorStop(1, 'transparent')
    
    context.fillStyle = gradient
    context.beginPath()
    context.arc(star.x, star.y, star.size, 0, Math.PI * 2)
    context.fill()
  })
}

const animate = () => {
  updateStars()
  drawStars()
  animationId = requestAnimationFrame(animate)
}

const handleResize = () => {
  setupCanvas()
  createStars()
}

const handleMouseMove = (e: MouseEvent) => {
  mouseX = e.clientX
  mouseY = e.clientY
}
</script>

<style scoped>
.starfield-canvas {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  z-index: -3;
  pointer-events: none;
}
</style> 