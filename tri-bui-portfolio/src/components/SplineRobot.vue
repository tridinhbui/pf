<template>
  <div class="spline-robot-container">
    <div class="robot-wrapper" ref="robotRef">
      <div class="spline-embed" id="spline-container">
        <!-- Spline will be injected here -->
      </div>
      
      <!-- Interactive UI Elements -->
      <div class="robot-controls">
        <button @click="animateRobot" class="control-btn pulse-btn">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor">
            <polygon points="5,3 19,12 5,21"></polygon>
          </svg>
          Activate NEXBOT
        </button>
        
        <div class="robot-status">
          <div class="status-indicator" :class="{ active: isActive }"></div>
          <span>{{ isActive ? 'Online' : 'Standby' }}</span>
        </div>
      </div>
      
      <!-- Holographic Effects -->
      <div class="hologram-effects">
        <div class="scan-line"></div>
        <div class="grid-overlay"></div>
        <div class="energy-rings">
          <div class="ring" v-for="n in 3" :key="n"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const robotRef = ref<HTMLElement>()
const isActive = ref(false)
let splineApp: any = null

const initializeSpline = async () => {
  // For now, use fallback robot since Spline URL is not provided
  console.log('Using fallback robot for demo')
  createFallbackRobot()
}

const createFallbackRobot = () => {
  const container = document.getElementById('spline-container')
  if (container) {
    container.innerHTML = `
      <div class="fallback-robot">
        <div class="robot-body">
          <div class="robot-head">
            <div class="eye left-eye"></div>
            <div class="eye right-eye"></div>
            <div class="antenna"></div>
          </div>
          <div class="robot-torso">
            <div class="chest-panel"></div>
          </div>
          <div class="robot-arms">
            <div class="arm left-arm"></div>
            <div class="arm right-arm"></div>
          </div>
        </div>
      </div>
    `
  }
}

const setupInteractions = () => {
  if (splineApp) {
    // Add mouse hover interactions
    splineApp.addEventListener('mouseHover', (e: any) => {
      if (e.target.name === 'Robot') {
        isActive.value = true
      }
    })
    
    splineApp.addEventListener('mouseDown', (e: any) => {
      animateRobot()
    })
  }
}

const animateRobot = () => {
  isActive.value = !isActive.value
  
  if (splineApp) {
    // Trigger robot animation
    splineApp.emitEvent('mouseDown', 'Robot')
  }
  
  // Trigger UI animations
  if (robotRef.value) {
    robotRef.value.classList.add('robot-activated')
    setTimeout(() => {
      robotRef.value?.classList.remove('robot-activated')
    }, 2000)
  }
}

onMounted(() => {
  setTimeout(() => {
    initializeSpline()
  }, 1000)
})

onUnmounted(() => {
  if (splineApp) {
    splineApp.dispose()
  }
})
</script>

<style scoped>
.spline-robot-container {
  position: relative;
  width: 100%;
  height: 500px;
  border-radius: 20px;
  overflow: hidden;
  background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
  border: 1px solid #dee2e6;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
}

.robot-wrapper {
  position: relative;
  width: 100%;
  height: 100%;
  transition: all 0.3s ease;
}

.robot-wrapper:hover {
  transform: scale(1.02);
  box-shadow: 0 15px 40px rgba(0, 0, 0, 0.15);
}

.spline-embed {
  width: 100%;
  height: 100%;
  position: relative;
  z-index: 1;
}

.spline-embed canvas {
  border-radius: 20px;
}

/* Fallback Robot Styles */
.fallback-robot {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  position: relative;
}

.robot-body {
  position: relative;
  animation: robot-float 4s ease-in-out infinite;
}

.robot-head {
  width: 80px;
  height: 80px;
  background: linear-gradient(135deg, #333333, #666666);
  border-radius: 15px;
  position: relative;
  margin: 0 auto 10px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
}

.eye {
  width: 12px;
  height: 12px;
  background: #00ff88;
  border-radius: 50%;
  position: absolute;
  top: 25px;
  animation: eye-blink 3s ease-in-out infinite;
  box-shadow: 0 0 10px #00ff88;
}

.left-eye { left: 20px; }
.right-eye { right: 20px; }

.antenna {
  width: 3px;
  height: 20px;
  background: #666666;
  position: absolute;
  top: -15px;
  left: 50%;
  margin-left: -1.5px;
}

.antenna::after {
  content: '';
  width: 8px;
  height: 8px;
  background: #ff4444;
  border-radius: 50%;
  position: absolute;
  top: -5px;
  left: -2.5px;
  animation: antenna-pulse 2s ease-in-out infinite;
}

.robot-torso {
  width: 100px;
  height: 120px;
  background: linear-gradient(135deg, #444444, #777777);
  border-radius: 10px;
  margin: 0 auto;
  position: relative;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
}

.chest-panel {
  width: 60px;
  height: 40px;
  background: linear-gradient(135deg, #222222, #555555);
  border-radius: 5px;
  position: absolute;
  top: 20px;
  left: 50%;
  margin-left: -30px;
  border: 2px solid #00ff88;
}

.robot-arms {
  position: absolute;
  top: 90px;
  width: 140px;
  left: -20px;
}

.arm {
  width: 25px;
  height: 80px;
  background: linear-gradient(135deg, #555555, #888888);
  border-radius: 12px;
  position: absolute;
  box-shadow: 0 3px 10px rgba(0, 0, 0, 0.2);
}

.left-arm {
  left: 0;
  animation: arm-wave 3s ease-in-out infinite;
}

.right-arm {
  right: 0;
  animation: arm-wave 3s ease-in-out infinite reverse;
}

/* Robot Controls */
.robot-controls {
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  align-items: center;
  gap: 15px;
  z-index: 10;
}

.control-btn {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 12px 24px;
  background: rgba(0, 0, 0, 0.8);
  color: white;
  border: none;
  border-radius: 25px;
  font-weight: 600;
  font-size: 14px;
  cursor: pointer;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.control-btn:hover {
  background: rgba(0, 0, 0, 0.9);
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
}

.control-btn svg {
  width: 16px;
  height: 16px;
}

.pulse-btn {
  animation: btn-pulse 2s ease-in-out infinite;
}

.robot-status {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 8px 16px;
  background: rgba(255, 255, 255, 0.9);
  border-radius: 20px;
  font-size: 12px;
  font-weight: 600;
  color: #333333;
  backdrop-filter: blur(10px);
}

.status-indicator {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: #ff4444;
  transition: all 0.3s ease;
}

.status-indicator.active {
  background: #00ff88;
  box-shadow: 0 0 10px #00ff88;
  animation: status-pulse 1s ease-in-out infinite;
}

/* Holographic Effects */
.hologram-effects {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 2;
}

.scan-line {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, transparent, #00ff88, transparent);
  opacity: 0;
  animation: scan-sweep 4s ease-in-out infinite;
}

.grid-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: 
    linear-gradient(rgba(0, 255, 136, 0.1) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0, 255, 136, 0.1) 1px, transparent 1px);
  background-size: 20px 20px;
  opacity: 0;
  transition: opacity 0.5s ease;
}

.robot-activated .grid-overlay {
  opacity: 1;
}

.energy-rings {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.ring {
  position: absolute;
  border: 2px solid #00ff88;
  border-radius: 50%;
  opacity: 0;
}

.ring:nth-child(1) {
  width: 100px;
  height: 100px;
  margin: -50px 0 0 -50px;
  animation: ring-expand 3s ease-out infinite;
}

.ring:nth-child(2) {
  width: 150px;
  height: 150px;
  margin: -75px 0 0 -75px;
  animation: ring-expand 3s ease-out infinite 0.5s;
}

.ring:nth-child(3) {
  width: 200px;
  height: 200px;
  margin: -100px 0 0 -100px;
  animation: ring-expand 3s ease-out infinite 1s;
}

.robot-activated .ring {
  animation-play-state: running;
}

/* Animations */
@keyframes robot-float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-10px); }
}

@keyframes eye-blink {
  0%, 90%, 100% { opacity: 1; }
  95% { opacity: 0; }
}

@keyframes antenna-pulse {
  0%, 100% { box-shadow: 0 0 5px #ff4444; }
  50% { box-shadow: 0 0 20px #ff4444; }
}

@keyframes arm-wave {
  0%, 100% { transform: rotate(0deg); }
  25% { transform: rotate(-15deg); }
  75% { transform: rotate(15deg); }
}

@keyframes btn-pulse {
  0%, 100% { box-shadow: 0 0 0 0 rgba(0, 0, 0, 0.4); }
  50% { box-shadow: 0 0 0 10px rgba(0, 0, 0, 0); }
}

@keyframes status-pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.2); }
}

@keyframes scan-sweep {
  0% { top: 0; opacity: 0; }
  10% { opacity: 1; }
  90% { opacity: 1; }
  100% { top: 100%; opacity: 0; }
}

@keyframes ring-expand {
  0% {
    transform: scale(0);
    opacity: 1;
  }
  100% {
    transform: scale(2);
    opacity: 0;
  }
}

/* Responsive */
@media (max-width: 768px) {
  .spline-robot-container {
    height: 350px;
  }
  
  .robot-controls {
    flex-direction: column;
    gap: 10px;
  }
  
  .control-btn {
    padding: 10px 20px;
    font-size: 12px;
  }
}
</style> 