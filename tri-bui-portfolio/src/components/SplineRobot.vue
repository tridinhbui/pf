<template>
  <div class="simple-robot-container">
    <!-- Simplified Control Panel -->
    <div class="robot-header">
      <div class="robot-status">
        <div class="status-badge" :class="{ 'online': isActive }">
          <div class="status-dot"></div>
          <span>{{ isActive ? 'ONLINE' : 'OFFLINE' }}</span>
        </div>
        <div class="robot-name">TRI AI ASSISTANT</div>
      </div>
      
      <div class="simple-controls">
        <button @click="toggleActive" class="control-btn" :class="{ 'active': isActive }">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor">
            <circle cx="12" cy="12" r="10"></circle>
            <polygon points="10,8 16,12 10,16 10,8"></polygon>
          </svg>
        </button>
        <button @click="speak" class="control-btn">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor">
            <polygon points="11 5 6 9 2 9 2 15 6 15 11 19 11 5"></polygon>
            <path d="m19.07 4.93-1.41 1.41A8.5 8.5 0 0 1 19 12a8.5 8.5 0 0 1-1.34 5.66l1.41 1.41A10.48 10.48 0 0 0 21 12a10.48 10.48 0 0 0-1.93-7.07z"></path>
          </svg>
        </button>
      </div>
    </div>

    <!-- 3D Robot Display -->
    <div class="robot-display">
      <div class="robot-scene" :class="{ 'active': isActive, 'speaking': isSpeaking }">
        <!-- New 3D Robot Design -->
        <div class="robot-3d">
          <!-- Robot Head -->
          <div class="robot-head">
            <div class="head-main">
              <div class="head-gradient"></div>
              <div class="head-highlights"></div>
            </div>
            
            <!-- Eyes -->
            <div class="robot-eyes">
              <div class="eye left">
                <div class="eye-core" :style="{ backgroundColor: eyeColor }"></div>
                <div class="eye-ring"></div>
              </div>
              <div class="eye right">
                <div class="eye-core" :style="{ backgroundColor: eyeColor }"></div>
                <div class="eye-ring"></div>
              </div>
            </div>
            
            <!-- Head Details -->
            <div class="head-antenna">
              <div class="antenna-base"></div>
              <div class="antenna-tip" :class="{ 'active': isActive }"></div>
            </div>
          </div>

          <!-- Robot Body -->
          <div class="robot-body">
            <div class="body-main">
              <div class="body-gradient"></div>
              <div class="body-panel">
                <div class="panel-lights">
                  <div class="light" v-for="n in 3" :key="n" :class="{ 'active': isActive }"></div>
                </div>
                <div class="central-core" :style="{ backgroundColor: eyeColor }"></div>
              </div>
            </div>
            
            <!-- Arms -->
            <div class="robot-arms">
              <div class="arm left">
                <div class="arm-segment upper"></div>
                <div class="arm-joint"></div>
                <div class="arm-segment lower"></div>
                <div class="hand"></div>
              </div>
              <div class="arm right">
                <div class="arm-segment upper"></div>
                <div class="arm-joint"></div>
                <div class="arm-segment lower"></div>
                <div class="hand"></div>
              </div>
            </div>
          </div>

          <!-- Floating Particles -->
          <div class="robot-particles" v-if="isActive">
            <div class="particle" v-for="n in 8" :key="n"></div>
          </div>
        </div>
      </div>
      
      <!-- Simple Info Display -->
      <div class="robot-info" v-if="isActive">
        <div class="info-text">{{ currentMessage }}</div>
        <div class="capabilities">
          <span v-for="skill in skills" :key="skill" class="skill-tag">{{ skill }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, onMounted } from 'vue'

const isActive = ref(false)
const isSpeaking = ref(false)
const currentMessage = ref("Hello! I'm Tri's AI assistant.")

const skills = ref([
  'Machine Learning',
  'Finance Analysis', 
  'Web Development',
  'Data Science'
])

const eyeColor = computed(() => {
  return isActive.value ? '#00ff88' : '#666666'
})

const messages = [
  "Hello! I'm Tri's AI assistant.",
  "I help with finance, technology, and entrepreneurship.",
  "Tri has built 5 ventures with 12K+ users.",
  "Let's explore Tri's portfolio together!"
]

let messageIndex = 0

const toggleActive = () => {
  isActive.value = !isActive.value
  if (isActive.value) {
    cycleMessages()
  }
}

const speak = () => {
  if (isActive.value) {
    isSpeaking.value = true
    setTimeout(() => {
      isSpeaking.value = false
    }, 2000)
  }
}

const cycleMessages = () => {
  if (isActive.value) {
    messageIndex = (messageIndex + 1) % messages.length
    currentMessage.value = messages[messageIndex]
    setTimeout(cycleMessages, 3000)
  }
}

onMounted(() => {
  setTimeout(() => {
    isActive.value = true
    cycleMessages()
  }, 1000)
})
</script>

<style scoped>
.simple-robot-container {
  max-width: 500px;
  margin: 0 auto;
  background: linear-gradient(135deg, #1a1a2e, #16213e);
  border-radius: 20px;
  padding: 1.5rem;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.robot-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1.5rem;
  padding-bottom: 1rem;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.robot-status {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.status-badge {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.5rem 1rem;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 20px;
  transition: all 0.3s ease;
}

.status-badge.online {
  background: rgba(0, 255, 136, 0.2);
  border: 1px solid #00ff88;
}

.status-dot {
  width: 8px;
  height: 8px;
  background: #666;
  border-radius: 50%;
  transition: all 0.3s ease;
}

.status-badge.online .status-dot {
  background: #00ff88;
  box-shadow: 0 0 10px #00ff88;
  animation: pulse 2s infinite;
}

.robot-name {
  color: #ffffff;
  font-size: 1.1rem;
  font-weight: 600;
  text-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
}

.simple-controls {
  display: flex;
  gap: 0.5rem;
}

.control-btn {
  width: 40px;
  height: 40px;
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 10px;
  color: #ffffff;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
}

.control-btn:hover {
  background: rgba(255, 255, 255, 0.2);
  transform: translateY(-2px);
}

.control-btn.active {
  background: rgba(0, 255, 136, 0.2);
  border-color: #00ff88;
  color: #00ff88;
}

.control-btn svg {
  width: 20px;
  height: 20px;
}

.robot-display {
  text-align: center;
}

.robot-scene {
  margin: 2rem 0;
  perspective: 1000px;
  transition: all 0.3s ease;
}

.robot-scene.active {
  transform: scale(1.05);
}

.robot-3d {
  position: relative;
  display: inline-block;
  transform-style: preserve-3d;
  animation: float 6s ease-in-out infinite;
}

.robot-scene.speaking .robot-3d {
  animation: speak-animation 0.5s ease-in-out infinite alternate;
}

/* Robot Head */
.robot-head {
  position: relative;
  width: 100px;
  height: 80px;
  margin: 0 auto 10px;
}

.head-main {
  width: 100%;
  height: 100%;
  background: linear-gradient(145deg, #4a90e2, #357abd);
  border-radius: 50px 50px 30px 30px;
  position: relative;
  box-shadow: 
    0 10px 20px rgba(0, 0, 0, 0.3),
    inset 0 5px 15px rgba(255, 255, 255, 0.2);
}

.head-gradient {
  position: absolute;
  top: 10%;
  left: 20%;
  width: 60%;
  height: 40%;
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.3), transparent);
  border-radius: 50%;
  filter: blur(5px);
}

.head-highlights {
  position: absolute;
  top: 15%;
  right: 20%;
  width: 15px;
  height: 15px;
  background: rgba(255, 255, 255, 0.6);
  border-radius: 50%;
  box-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
}

.robot-eyes {
  position: absolute;
  top: 30%;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 20px;
}

.eye {
  width: 20px;
  height: 20px;
  background: #000;
  border-radius: 50%;
  position: relative;
  overflow: hidden;
}

.eye-core {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  transition: all 0.3s ease;
  animation: eye-glow 2s ease-in-out infinite alternate;
}

.eye-ring {
  position: absolute;
  top: -2px;
  left: -2px;
  right: -2px;
  bottom: -2px;
  border: 1px solid rgba(255, 255, 255, 0.3);
  border-radius: 50%;
}

.head-antenna {
  position: absolute;
  top: -10px;
  left: 50%;
  transform: translateX(-50%);
}

.antenna-base {
  width: 6px;
  height: 15px;
  background: linear-gradient(to top, #357abd, #4a90e2);
  border-radius: 3px;
}

.antenna-tip {
  width: 8px;
  height: 8px;
  background: #666;
  border-radius: 50%;
  margin: -2px auto 0;
  transition: all 0.3s ease;
}

.antenna-tip.active {
  background: #00ff88;
  box-shadow: 0 0 15px #00ff88;
  animation: antenna-pulse 1.5s ease-in-out infinite;
}

/* Robot Body */
.robot-body {
  position: relative;
  margin: 0 auto;
}

.body-main {
  width: 120px;
  height: 140px;
  background: linear-gradient(145deg, #4a90e2, #357abd);
  border-radius: 20px;
  position: relative;
  margin: 0 auto;
  box-shadow: 
    0 15px 30px rgba(0, 0, 0, 0.3),
    inset 0 5px 15px rgba(255, 255, 255, 0.2);
}

.body-gradient {
  position: absolute;
  top: 10%;
  left: 15%;
  width: 70%;
  height: 50%;
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.2), transparent);
  border-radius: 20px;
  filter: blur(3px);
}

.body-panel {
  position: absolute;
  top: 30%;
  left: 50%;
  transform: translateX(-50%);
  width: 80px;
  height: 60px;
  background: rgba(0, 0, 0, 0.2);
  border-radius: 10px;
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.panel-lights {
  display: flex;
  justify-content: center;
  gap: 8px;
  margin: 10px 0;
}

.light {
  width: 6px;
  height: 6px;
  background: #333;
  border-radius: 50%;
  transition: all 0.3s ease;
}

.light.active {
  background: #00ff88;
  box-shadow: 0 0 8px #00ff88;
}

.central-core {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  margin: 5px auto;
  transition: all 0.3s ease;
  animation: core-pulse 3s ease-in-out infinite;
}

/* Robot Arms */
.robot-arms {
  position: absolute;
  top: 20px;
  width: 100%;
  height: 100px;
}

.arm {
  position: absolute;
  top: 0;
}

.arm.left {
  left: -30px;
  animation: arm-move-left 4s ease-in-out infinite;
}

.arm.right {
  right: -30px;
  animation: arm-move-right 4s ease-in-out infinite;
}

.arm-segment {
  width: 12px;
  height: 40px;
  background: linear-gradient(145deg, #4a90e2, #357abd);
  border-radius: 6px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
}

.arm-joint {
  width: 16px;
  height: 16px;
  background: linear-gradient(145deg, #357abd, #2a5d8f);
  border-radius: 50%;
  margin: -2px auto;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.3);
}

.hand {
  width: 14px;
  height: 14px;
  background: linear-gradient(145deg, #4a90e2, #357abd);
  border-radius: 50%;
  margin: 5px auto 0;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
}

/* Particles */
.robot-particles {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
}

.particle {
  position: absolute;
  width: 4px;
  height: 4px;
  background: #00ff88;
  border-radius: 50%;
  animation: particle-float 3s ease-in-out infinite;
}

.particle:nth-child(1) { top: 20%; left: 10%; animation-delay: 0s; }
.particle:nth-child(2) { top: 40%; right: 15%; animation-delay: 0.5s; }
.particle:nth-child(3) { top: 60%; left: 20%; animation-delay: 1s; }
.particle:nth-child(4) { top: 80%; right: 25%; animation-delay: 1.5s; }
.particle:nth-child(5) { top: 30%; left: 80%; animation-delay: 2s; }
.particle:nth-child(6) { top: 70%; right: 80%; animation-delay: 2.5s; }
.particle:nth-child(7) { top: 10%; left: 50%; animation-delay: 3s; }
.particle:nth-child(8) { top: 90%; right: 50%; animation-delay: 3.5s; }

/* Info Display */
.robot-info {
  margin-top: 1.5rem;
  padding: 1rem;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 15px;
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.info-text {
  color: #ffffff;
  font-size: 1rem;
  margin-bottom: 1rem;
  text-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
}

.capabilities {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  justify-content: center;
}

.skill-tag {
  padding: 0.25rem 0.75rem;
  background: rgba(0, 255, 136, 0.2);
  border: 1px solid #00ff88;
  border-radius: 15px;
  color: #00ff88;
  font-size: 0.8rem;
  font-weight: 500;
}

/* Animations */
@keyframes float {
  0%, 100% { transform: translateY(0) rotateY(0deg); }
  50% { transform: translateY(-10px) rotateY(5deg); }
}

@keyframes speak-animation {
  0% { transform: scale(1); }
  100% { transform: scale(1.05); }
}

@keyframes pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.5; }
}

@keyframes eye-glow {
  0% { box-shadow: 0 0 5px currentColor; }
  100% { box-shadow: 0 0 15px currentColor; }
}

@keyframes antenna-pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.2); }
}

@keyframes core-pulse {
  0%, 100% { opacity: 0.8; transform: scale(1); }
  50% { opacity: 1; transform: scale(1.1); }
}

@keyframes arm-move-left {
  0%, 100% { transform: rotate(-10deg); }
  50% { transform: rotate(-20deg); }
}

@keyframes arm-move-right {
  0%, 100% { transform: rotate(10deg); }
  50% { transform: rotate(20deg); }
}

@keyframes particle-float {
  0%, 100% { transform: translateY(0) scale(1); opacity: 0.6; }
  50% { transform: translateY(-20px) scale(1.2); opacity: 1; }
}

/* Responsive */
@media (max-width: 768px) {
  .simple-robot-container {
    max-width: 400px;
    padding: 1rem;
  }
  
  .robot-3d {
    transform: scale(0.8);
  }
  
  .robot-name {
    font-size: 1rem;
  }
  
  .info-text {
    font-size: 0.9rem;
  }
}
</style> 