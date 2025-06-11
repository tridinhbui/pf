<template>
  <div class="optimus-robot-container">
    <!-- Universe Background -->
    <div class="universe-background">
      <div class="stars-layer">
        <div class="star" v-for="n in 50" :key="n"></div>
        </div>
      <div class="nebula-clouds">
        <div class="nebula" v-for="n in 3" :key="n"></div>
          </div>
      <div class="cosmic-particles">
        <div class="cosmic-particle" v-for="n in 15" :key="n"></div>
        </div>
      </div>
      
    <!-- Simplified Control Panel -->
    <div class="robot-header">
      <div class="robot-status">
        <div class="status-badge online">
          <div class="status-dot"></div>
          <span>ONLINE</span>
      </div>
        <div class="robot-name">OPTIMUS AI</div>
    </div>

      <div class="system-stats">
        <div class="stat-item">
          <span class="stat-label">PWR</span>
          <div class="stat-bar">
            <div class="stat-fill" :style="{ width: power + '%' }"></div>
          </div>
              </div>
        <div class="stat-item">
          <span class="stat-label">SYS</span>
          <div class="stat-bar">
            <div class="stat-fill" :style="{ width: systemHealth + '%' }"></div>
                    </div>
                  </div>
                </div>
      
      <!-- Mute Button -->
      <div class="robot-controls">
        <button 
          @click="toggleMute" 
          class="mute-btn" 
          :class="{ 'muted': isMuted }"
          :title="isMuted ? 'Unmute Robot Voice' : 'Mute Robot Voice'"
        >
          <span v-if="!isMuted">🔊</span>
          <span v-else>🔇</span>
        </button>
                </div>
              </div>
              
    <!-- Tesla Optimus Style Robot -->
    <div class="robot-display">
      <div class="robot-scene active">
        <!-- Optimus Robot Design -->
        <div class="optimus-robot">
          <!-- Robot Head - Tesla Style -->
          <div class="optimus-head">
            <div class="head-chassis">
              <div class="head-shell"></div>
              <div class="head-visor">
                <div class="visor-strip"></div>
              </div>
              
              <!-- Dangerous Eyes -->
              <div class="optimus-eyes">
                <div class="eye-scanner left">
                  <div class="scanner-beam"></div>
                  <div class="eye-lens"></div>
                </div>
                <div class="eye-scanner right">
                  <div class="scanner-beam"></div>
                  <div class="eye-lens"></div>
              </div>
            </div>

              <!-- Head Details -->
              <div class="head-grilles">
                <div class="grille" v-for="n in 4" :key="n"></div>
                </div>
              </div>
              
            <!-- Neck Joint */
            <div class="neck-joint">
              <div class="neck-servo"></div>
                </div>
                </div>

          <!-- Robot Torso - Humanoid Design -->
          <div class="optimus-torso">
            <div class="chest-chassis">
              <div class="chest-plate">
                <div class="central-core">
                  <div class="core-ring"></div>
                  <div class="core-center"></div>
              </div>
              
                <!-- Status Lights -->
                <div class="status-panel">
                  <div class="status-light" v-for="n in 6" :key="n" :class="{ 'active': n <= activeStatusLights }"></div>
                </div>
                
                <!-- Chest Vents -->
                <div class="chest-vents">
                  <div class="vent-line" v-for="n in 8" :key="n"></div>
        </div>
      </div>

              <!-- Shoulder Joints -->
              <div class="shoulder-joints">
                <div class="shoulder left">
                  <div class="shoulder-plate"></div>
                  <div class="shoulder-servo"></div>
          </div>
                <div class="shoulder right">
                  <div class="shoulder-plate"></div>
                  <div class="shoulder-servo"></div>
                </div>
              </div>
                </div>
              </div>

          <!-- Robot Arms - Mechanical Design -->
          <div class="optimus-arms">
            <div class="arm left-arm">
              <div class="upper-arm">
                <div class="arm-chassis"></div>
                <div class="arm-actuators">
                  <div class="actuator" v-for="n in 3" :key="n"></div>
                </div>
              </div>
              <div class="elbow-joint">
                <div class="joint-housing"></div>
                <div class="joint-servo"></div>
                </div>
              <div class="forearm">
                <div class="forearm-chassis"></div>
                <div class="wrist-joint"></div>
              </div>
              <div class="hand">
                <div class="palm"></div>
                <div class="fingers">
                  <div class="finger" v-for="n in 4" :key="n"></div>
                  <div class="thumb"></div>
            </div>
          </div>
        </div>

            <div class="arm right-arm">
              <div class="upper-arm">
                <div class="arm-chassis"></div>
                <div class="arm-actuators">
                  <div class="actuator" v-for="n in 3" :key="n"></div>
          </div>
                </div>
              <div class="elbow-joint">
                <div class="joint-housing"></div>
                <div class="joint-servo"></div>
              </div>
              <div class="forearm">
                <div class="forearm-chassis"></div>
                <div class="wrist-joint"></div>
            </div>
              <div class="hand">
                <div class="palm"></div>
                <div class="fingers">
                  <div class="finger" v-for="n in 4" :key="n"></div>
                  <div class="thumb"></div>
          </div>
        </div>
              </div>
            </div>
            
          <!-- Energy Field Effects -->
          <div class="energy-field">
            <div class="field-ring" v-for="n in 3" :key="n"></div>
        </div>

          <!-- Floating Data Streams -->
          <div class="data-streams">
            <div class="data-stream" v-for="n in 6" :key="n">
              <div class="data-chunk" v-for="m in 4" :key="m"></div>
          </div>
                </div>
              </div>
            </div>
            
      <!-- AI Information Display -->
              <div class="robot-info">
        <div class="info-display">
          <div class="info-text">
            {{ currentMessage }}
            <button 
              @click="toggleMute" 
              class="inline-mute-btn" 
              :class="{ 'muted': isMuted }"
              :title="isMuted ? 'Unmute Robot Voice' : 'Mute Robot Voice'"
            >
              <span v-if="!isMuted">🔊</span>
              <span v-else>🔇</span>
            </button>
            <button 
              @click="speakCurrentMessage" 
              class="speak-btn"
              :disabled="isMuted"
              title="Speak Current Message"
            >
              🗣️
            </button>
              </div>
          <div class="threat-level">
            <span class="threat-label">THREAT LEVEL:</span>
            <span class="threat-value" :class="threatClass">{{ threatLevel }}</span>
      </div>
    </div>

        <div class="capabilities">
          <span v-for="skill in skills" :key="skill" class="skill-tag">{{ skill }}</span>
        </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, onMounted } from 'vue'

const power = ref(95)
const systemHealth = ref(100)
const activeStatusLights = ref(6)
const currentMessage = ref("OPTIMUS AI SYSTEM ONLINE")
const threatLevel = ref("TACTICAL")
const isMuted = ref(false)
const isCurrentlySpeaking = ref(false)

const skills = ref([
  'AUTONOMOUS SYSTEMS',
  'QUANTUM PROCESSING', 
  'STRATEGIC ANALYSIS',
  'THREAT ASSESSMENT'
])

const threatClass = computed(() => {
  return threatLevel.value === 'TACTICAL' ? 'threat-tactical' : 'threat-high'
})

const messages = [
  "OPTIMUS AI SYSTEM ONLINE",
  "ANALYZING PORTFOLIO DATA...",
  "TRI'S VENTURES: 5 ACTIVE SYSTEMS",
  "USER BASE: 12,000+ MONITORED",
  "FINANCIAL ASSETS: $350M+ TRACKED",
  "THREAT ASSESSMENT: MINIMAL",
  "READY FOR DEPLOYMENT"
]

let messageIndex = 0

// Text-to-Speech functionality
const speakText = (text: string) => {
  if (isMuted.value || isCurrentlySpeaking.value) return
  
  isCurrentlySpeaking.value = true
  const utterance = new SpeechSynthesisUtterance(text)
  
  // Slow down speech
  utterance.rate = 0.7 // Slower speech rate
  utterance.pitch = 0.8 // Slightly lower pitch for robot effect
  utterance.volume = 0.8
  
  utterance.onend = () => {
    isCurrentlySpeaking.value = false
  }
  
  utterance.onerror = () => {
    isCurrentlySpeaking.value = false
  }
  
  speechSynthesis.speak(utterance)
}

const toggleMute = () => {
  isMuted.value = !isMuted.value
  if (isMuted.value && isCurrentlySpeaking.value) {
    speechSynthesis.cancel()
    isCurrentlySpeaking.value = false
  }
}

const speakCurrentMessage = () => {
  speakText(currentMessage.value)
}

const cycleMessages = () => {
  messageIndex = (messageIndex + 1) % messages.length
  const newMessage = messages[messageIndex]
  currentMessage.value = newMessage
  
  // Auto-speak the message if not muted
  if (!isMuted.value) {
    setTimeout(() => {
      speakText(newMessage)
    }, 500) // Small delay before speaking
  }
  
  // Update threat level occasionally
  if (Math.random() < 0.3) {
    threatLevel.value = Math.random() < 0.7 ? 'TACTICAL' : 'HIGH ALERT'
  }
  
  setTimeout(cycleMessages, 6000) // Slower cycle - 6 seconds instead of 4
}

const updateSystemStats = () => {
  power.value = Math.max(90, Math.min(100, power.value + (Math.random() - 0.5) * 3))
  systemHealth.value = Math.max(95, Math.min(100, systemHealth.value + (Math.random() - 0.5) * 2))
  activeStatusLights.value = Math.floor(Math.random() * 3) + 4 // 4-6 lights active
}

onMounted(() => {
  // Start immediately - no activation needed
  setTimeout(() => {
    cycleMessages()
  }, 1000)
  
  // Update stats periodically
  setInterval(updateSystemStats, 3000)
})
</script>

<style scoped>
.optimus-robot-container {
  max-width: 600px;
  margin: 0 auto;
  background: linear-gradient(135deg, #0a0a0a, #1a1a1a);
  border-radius: 20px;
  padding: 1.5rem;
  box-shadow: 
    0 25px 50px rgba(0, 0, 0, 0.5),
    inset 0 1px 0 rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(100, 100, 100, 0.2);
  position: relative;
  overflow: hidden;
}

/* Universe Background */
.universe-background {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: 
    radial-gradient(ellipse at center, rgba(50, 50, 100, 0.3) 0%, transparent 70%),
    radial-gradient(ellipse at 20% 80%, rgba(100, 50, 150, 0.2) 0%, transparent 50%),
    radial-gradient(ellipse at 80% 20%, rgba(50, 100, 150, 0.2) 0%, transparent 50%),
    linear-gradient(45deg, #000000, #0a0a0a);
  border-radius: 20px;
}

.stars-layer {
  position: absolute;
  width: 100%;
  height: 100%;
}

.star {
  position: absolute;
  width: 2px;
  height: 2px;
  background: #ffffff;
  border-radius: 50%;
  animation: star-twinkle 3s ease-in-out infinite;
}

.star:nth-child(odd) {
  animation-duration: 2s;
  background: #ccccff;
}

.star:nth-child(1) { top: 10%; left: 20%; }
.star:nth-child(2) { top: 20%; left: 80%; animation-delay: 0.5s; }
.star:nth-child(3) { top: 30%; left: 15%; animation-delay: 1s; }
.star:nth-child(4) { top: 40%; left: 90%; animation-delay: 1.5s; }
.star:nth-child(5) { top: 50%; left: 10%; animation-delay: 2s; }
.star:nth-child(6) { top: 60%; left: 75%; animation-delay: 2.5s; }
.star:nth-child(7) { top: 70%; left: 25%; animation-delay: 3s; }
.star:nth-child(8) { top: 80%; left: 85%; animation-delay: 3.5s; }
.star:nth-child(9) { top: 90%; left: 45%; animation-delay: 4s; }
.star:nth-child(10) { top: 15%; left: 60%; animation-delay: 4.5s; }

.nebula-clouds {
  position: absolute;
  width: 100%;
  height: 100%;
}

.nebula {
  position: absolute;
  border-radius: 50%;
  filter: blur(40px);
  opacity: 0.1;
  animation: nebula-drift 20s ease-in-out infinite;
}

.nebula:nth-child(1) {
  width: 200px;
  height: 100px;
  background: rgba(100, 50, 200, 0.3);
  top: 20%;
  left: -10%;
}

.nebula:nth-child(2) {
  width: 150px;
  height: 150px;
  background: rgba(50, 100, 200, 0.3);
  top: 60%;
  right: -10%;
  animation-delay: 5s;
}

.nebula:nth-child(3) {
  width: 100px;
  height: 200px;
  background: rgba(200, 50, 100, 0.3);
  top: 40%;
  left: 50%;
  animation-delay: 10s;
}

.cosmic-particles {
  position: absolute;
  width: 100%;
  height: 100%;
}

.cosmic-particle {
  position: absolute;
  width: 1px;
  height: 1px;
  background: rgba(255, 255, 255, 0.6);
  border-radius: 50%;
  animation: cosmic-drift 8s linear infinite;
}

.robot-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1.5rem;
  padding: 1rem;
  background: rgba(0, 0, 0, 0.8);
  border: 1px solid rgba(100, 100, 100, 0.3);
  border-radius: 10px;
  backdrop-filter: blur(10px);
  position: relative;
  z-index: 2;
}

.robot-controls {
  display: flex;
  gap: 0.5rem;
}

.mute-btn {
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.2);
  color: #ffffff;
  padding: 0.5rem;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s ease;
  font-size: 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  min-width: 40px;
  height: 40px;
}

.mute-btn:hover {
  background: rgba(255, 255, 255, 0.2);
  border-color: rgba(255, 255, 255, 0.4);
}

.mute-btn.muted {
  background: rgba(255, 68, 68, 0.2);
  border-color: #ff4444;
}

.inline-mute-btn, .speak-btn {
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.2);
  color: #ffffff;
  padding: 0.25rem 0.5rem;
  border-radius: 4px;
  cursor: pointer;
  transition: all 0.3s ease;
  font-size: 0.75rem;
  margin-left: 0.5rem;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  min-width: 30px;
  height: 24px;
}

.inline-mute-btn:hover, .speak-btn:hover {
  background: rgba(255, 255, 255, 0.2);
  border-color: rgba(255, 255, 255, 0.4);
}

.inline-mute-btn.muted {
  background: rgba(255, 68, 68, 0.2);
  border-color: #ff4444;
}

.speak-btn:disabled {
  opacity: 0.5;
  cursor: not-allowed;
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
  background: rgba(255, 0, 0, 0.2);
  border: 1px solid #ff4444;
  border-radius: 20px;
}

.status-badge.online {
  background: rgba(0, 255, 0, 0.2);
  border-color: #44ff44;
}

.status-dot {
  width: 8px;
  height: 8px;
  background: #44ff44;
  border-radius: 50%;
  box-shadow: 0 0 10px #44ff44;
  animation: danger-pulse 1.5s ease-in-out infinite;
}

.robot-name {
  color: #ffffff;
  font-size: 1.2rem;
  font-weight: 700;
  text-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
  letter-spacing: 0.1em;
}

.system-stats {
  display: flex;
  gap: 1rem;
}

.stat-item {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.stat-label {
  color: #cccccc;
  font-size: 0.8rem;
  font-weight: 600;
  min-width: 30px;
}

.stat-bar {
  width: 40px;
  height: 4px;
  background: rgba(100, 100, 100, 0.3);
  border-radius: 2px;
  overflow: hidden;
}

.stat-fill {
  height: 100%;
  background: linear-gradient(90deg, #ff4444, #44ff44);
  transition: width 0.3s ease;
  box-shadow: 0 0 8px rgba(68, 255, 68, 0.5);
}

.robot-display {
  text-align: center;
  position: relative;
  z-index: 2;
}

.robot-scene {
  margin: 2rem 0;
  perspective: 1200px;
}

.optimus-robot {
  position: relative;
  display: inline-block;
  transform-style: preserve-3d;
  animation: optimus-hover 8s ease-in-out infinite;
  filter: drop-shadow(0 10px 20px rgba(0, 0, 0, 0.3));
}

/* Optimus Head */
.optimus-head {
  position: relative;
  width: 120px;
  height: 100px;
  margin: 0 auto 15px;
}

.head-chassis {
  width: 100%;
  height: 100%;
  position: relative;
}

.head-shell {
  width: 100%;
  height: 100%;
  background: 
    linear-gradient(145deg, #f0f0f0, #d0d0d0),
    linear-gradient(45deg, rgba(255, 255, 255, 0.2), transparent);
  border-radius: 15px 15px 25px 25px;
  position: relative;
  box-shadow: 
    0 8px 16px rgba(0, 0, 0, 0.3),
    inset 0 2px 4px rgba(255, 255, 255, 0.3),
    inset 0 -2px 4px rgba(0, 0, 0, 0.2);
  border: 1px solid rgba(0, 0, 0, 0.1);
}

.head-visor {
  position: absolute;
  top: 25%;
  left: 15%;
  width: 70%;
  height: 15px;
  background: linear-gradient(90deg, #000, #333, #000);
  border-radius: 8px;
  box-shadow: 
    inset 0 2px 4px rgba(0, 0, 0, 0.8),
    0 0 10px rgba(255, 0, 0, 0.3);
}

.visor-strip {
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, transparent, #ff4444, transparent);
  margin-top: 6px;
  animation: visor-scan 3s linear infinite;
}

.optimus-eyes {
  position: absolute;
  top: 45%;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 25px;
}

.eye-scanner {
  width: 18px;
  height: 18px;
  background: radial-gradient(circle, #ff0000, #990000);
  border-radius: 50%;
  position: relative;
  box-shadow: 
    0 0 15px #ff0000,
    inset 0 2px 4px rgba(0, 0, 0, 0.5);
  animation: eye-threat-glow 2s ease-in-out infinite alternate;
}

.scanner-beam {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 2px;
  height: 2px;
  background: #ffffff;
  border-radius: 50%;
  transform: translate(-50%, -50%);
  box-shadow: 0 0 8px #ffffff;
  animation: scanner-pulse 1s ease-in-out infinite;
}

.eye-lens {
  position: absolute;
  top: 2px;
  left: 2px;
  right: 2px;
  bottom: 2px;
  border: 1px solid rgba(255, 255, 255, 0.3);
  border-radius: 50%;
}

.head-grilles {
  position: absolute;
  bottom: 10%;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 3px;
}

.grille {
  width: 2px;
  height: 12px;
  background: linear-gradient(to bottom, #666, #333);
  border-radius: 1px;
}

.neck-joint {
  position: absolute;
  bottom: -8px;
  left: 50%;
  transform: translateX(-50%);
  width: 40px;
  height: 16px;
  background: linear-gradient(145deg, #e0e0e0, #c0c0c0);
  border-radius: 8px;
  border: 1px solid rgba(0, 0, 0, 0.2);
}

.neck-servo {
  width: 20px;
  height: 8px;
  background: linear-gradient(145deg, #333, #111);
  border-radius: 4px;
  margin: 4px auto;
  border: 1px solid rgba(0, 0, 0, 0.3);
}

/* Optimus Torso */
.optimus-torso {
  position: relative;
  margin: 0 auto 20px;
}

.chest-chassis {
  width: 140px;
  height: 160px;
  background: 
    linear-gradient(145deg, #f5f5f5, #e0e0e0),
    radial-gradient(circle at 30% 30%, rgba(255, 255, 255, 0.3), transparent);
  border-radius: 25px;
  position: relative;
  margin: 0 auto;
  box-shadow: 
    0 15px 30px rgba(0, 0, 0, 0.3),
    inset 0 3px 6px rgba(255, 255, 255, 0.3),
    inset 0 -3px 6px rgba(0, 0, 0, 0.2);
  border: 1px solid rgba(0, 0, 0, 0.1);
}

.chest-plate {
  position: absolute;
  top: 20%;
  left: 50%;
  transform: translateX(-50%);
  width: 100px;
  height: 100px;
  background: rgba(0, 0, 0, 0.1);
  border-radius: 15px;
  border: 1px solid rgba(0, 0, 0, 0.2);
}

.central-core {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 50px;
  height: 50px;
}

.core-ring {
  width: 100%;
  height: 100%;
  border: 3px solid #333;
  border-radius: 50%;
  position: relative;
  animation: core-rotation 4s linear infinite;
}

.core-center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 20px;
  height: 20px;
  background: radial-gradient(circle, #ff4444, #990000);
  border-radius: 50%;
  box-shadow: 0 0 20px #ff4444;
  animation: core-pulse-danger 2s ease-in-out infinite;
}

.status-panel {
  position: absolute;
  top: 10px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 4px;
}

.status-light {
  width: 4px;
  height: 4px;
  background: #333;
  border-radius: 50%;
  transition: all 0.3s ease;
}

.status-light.active {
  background: #44ff44;
  box-shadow: 0 0 6px #44ff44;
}

.chest-vents {
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  gap: 2px;
}

.vent-line {
  width: 40px;
  height: 1px;
  background: linear-gradient(90deg, transparent, #666, transparent);
}

/* Shoulder Joints */
.shoulder-joints {
  position: absolute;
  top: 10%;
  width: 100%;
  height: 60px;
}

.shoulder {
  position: absolute;
  top: 0;
  width: 35px;
  height: 35px;
}

.shoulder.left {
  left: -20px;
}

.shoulder.right {
  right: -20px;
}

.shoulder-plate {
  width: 100%;
  height: 100%;
  background: linear-gradient(145deg, #e0e0e0, #c0c0c0);
  border-radius: 50%;
  border: 1px solid rgba(0, 0, 0, 0.2);
  box-shadow: 
    0 4px 8px rgba(0, 0, 0, 0.2),
    inset 0 2px 4px rgba(255, 255, 255, 0.3);
}

.shoulder-servo {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 15px;
  height: 15px;
  background: linear-gradient(145deg, #333, #111);
  border-radius: 50%;
  border: 1px solid rgba(0, 0, 0, 0.3);
}

/* Optimus Arms */
.optimus-arms {
  position: absolute;
  top: 30px;
  width: 100%;
  height: 120px;
}

.arm {
  position: absolute;
  top: 0;
}

.left-arm {
  left: -60px;
  animation: arm-servo-left 6s ease-in-out infinite;
}

.right-arm {
  right: -60px;
  animation: arm-servo-right 6s ease-in-out infinite;
}

.upper-arm {
  width: 20px;
  height: 50px;
  background: linear-gradient(145deg, #e0e0e0, #c0c0c0);
  border-radius: 10px;
  position: relative;
  border: 1px solid rgba(0, 0, 0, 0.2);
  box-shadow: 
    0 4px 8px rgba(0, 0, 0, 0.2),
    inset 0 2px 4px rgba(255, 255, 255, 0.2);
}

.arm-chassis {
  width: 100%;
  height: 100%;
  background: linear-gradient(145deg, #f0f0f0, #d0d0d0);
  border-radius: 10px;
}

.arm-actuators {
  position: absolute;
  right: -3px;
  top: 10%;
  display: flex;
  flex-direction: column;
  gap: 3px;
}

.actuator {
  width: 6px;
  height: 8px;
  background: linear-gradient(145deg, #333, #111);
  border-radius: 2px;
  border: 1px solid rgba(0, 0, 0, 0.3);
}

.elbow-joint {
  width: 24px;
  height: 24px;
  background: linear-gradient(145deg, #d0d0d0, #b0b0b0);
  border-radius: 50%;
  margin: -2px auto;
  position: relative;
  border: 1px solid rgba(0, 0, 0, 0.2);
  box-shadow: 
    0 4px 8px rgba(0, 0, 0, 0.3),
    inset 0 2px 4px rgba(255, 255, 255, 0.3);
}

.joint-housing {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  background: linear-gradient(145deg, #e0e0e0, #c0c0c0);
}

.joint-servo {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 10px;
  height: 10px;
  background: linear-gradient(145deg, #333, #111);
  border-radius: 50%;
  border: 1px solid rgba(0, 0, 0, 0.3);
}

.forearm {
  width: 18px;
  height: 40px;
  background: linear-gradient(145deg, #e0e0e0, #c0c0c0);
  border-radius: 8px;
  margin: 5px auto 0;
  position: relative;
  border: 1px solid rgba(0, 0, 0, 0.2);
  box-shadow: 
    0 4px 8px rgba(0, 0, 0, 0.2),
    inset 0 2px 4px rgba(255, 255, 255, 0.2);
}

.forearm-chassis {
  width: 100%;
  height: 100%;
  background: linear-gradient(145deg, #f0f0f0, #d0d0d0);
  border-radius: 8px;
}

.wrist-joint {
  position: absolute;
  bottom: -3px;
  left: 50%;
  transform: translateX(-50%);
  width: 12px;
  height: 6px;
  background: linear-gradient(145deg, #333, #111);
  border-radius: 3px;
  border: 1px solid rgba(0, 0, 0, 0.3);
}

.hand {
  width: 16px;
  height: 20px;
  background: linear-gradient(145deg, #e0e0e0, #c0c0c0);
  border-radius: 8px 8px 4px 4px;
  margin: 8px auto 0;
  position: relative;
  border: 1px solid rgba(0, 0, 0, 0.2);
  box-shadow: 
    0 2px 4px rgba(0, 0, 0, 0.2),
    inset 0 1px 2px rgba(255, 255, 255, 0.2);
}

.palm {
  width: 100%;
  height: 70%;
  background: linear-gradient(145deg, #f0f0f0, #d0d0d0);
  border-radius: 6px 6px 2px 2px;
}

.fingers {
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 1px;
}

.finger {
  width: 2px;
  height: 6px;
  background: linear-gradient(145deg, #d0d0d0, #b0b0b0);
  border-radius: 1px;
}

.thumb {
  position: absolute;
  left: -2px;
  top: -3px;
  width: 2px;
  height: 4px;
  background: linear-gradient(145deg, #d0d0d0, #b0b0b0);
  border-radius: 1px;
}

/* Energy Field */
.energy-field {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 200px;
  height: 200px;
  pointer-events: none;
}

.field-ring {
  position: absolute;
  top: 50%;
  left: 50%;
  border: 1px solid rgba(255, 68, 68, 0.3);
  border-radius: 50%;
  animation: field-pulse 4s ease-in-out infinite;
}

.field-ring:nth-child(1) {
  width: 120px;
  height: 120px;
  margin: -60px 0 0 -60px;
  animation-delay: 0s;
}

.field-ring:nth-child(2) {
  width: 160px;
  height: 160px;
  margin: -80px 0 0 -80px;
  animation-delay: 1s;
}

.field-ring:nth-child(3) {
  width: 200px;
  height: 200px;
  margin: -100px 0 0 -100px;
  animation-delay: 2s;
}

/* Data Streams */
.data-streams {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
}

.data-stream {
  position: absolute;
  display: flex;
  flex-direction: column;
  gap: 4px;
  animation: data-float 6s ease-in-out infinite;
}

.data-stream:nth-child(1) { top: 10%; left: 5%; animation-delay: 0s; }
.data-stream:nth-child(2) { top: 20%; right: 10%; animation-delay: 1s; }
.data-stream:nth-child(3) { top: 60%; left: 15%; animation-delay: 2s; }
.data-stream:nth-child(4) { top: 70%; right: 5%; animation-delay: 3s; }
.data-stream:nth-child(5) { top: 40%; left: 85%; animation-delay: 4s; }
.data-stream:nth-child(6) { top: 80%; left: 50%; animation-delay: 5s; }

.data-chunk {
  width: 3px;
  height: 3px;
  background: rgba(255, 68, 68, 0.8);
  border-radius: 1px;
  animation: data-pulse 2s ease-in-out infinite;
}

/* Robot Info */
.robot-info {
  margin-top: 1.5rem;
  position: relative;
  z-index: 2;
}

.info-display {
  padding: 1rem;
  background: rgba(0, 0, 0, 0.8);
  border: 1px solid rgba(100, 100, 100, 0.3);
  border-radius: 10px;
  margin-bottom: 1rem;
  backdrop-filter: blur(10px);
}

.info-text {
  color: #ffffff;
  font-size: 1rem;
  margin-bottom: 0.5rem;
  text-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
  font-weight: 600;
  letter-spacing: 0.05em;
}

.threat-level {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.threat-label {
  color: #cccccc;
  font-size: 0.8rem;
  font-weight: 600;
}

.threat-value {
  font-size: 0.9rem;
  font-weight: 700;
  letter-spacing: 0.1em;
}

.threat-tactical {
  color: #44ff44;
  text-shadow: 0 0 5px #44ff44;
}

.threat-high {
  color: #ff4444;
  text-shadow: 0 0 5px #ff4444;
  animation: threat-blink 1s ease-in-out infinite;
}

.capabilities {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  justify-content: center;
}

.skill-tag {
  padding: 0.25rem 0.75rem;
  background: rgba(255, 68, 68, 0.2);
  border: 1px solid #ff4444;
  border-radius: 15px;
  color: #ff4444;
  font-size: 0.8rem;
  font-weight: 600;
  letter-spacing: 0.05em;
  text-shadow: 0 0 5px rgba(255, 68, 68, 0.3);
}

/* Animations */
@keyframes optimus-hover {
  0%, 100% { transform: translateY(0) rotateY(0deg) rotateX(0deg); }
  25% { transform: translateY(-8px) rotateY(2deg) rotateX(1deg); }
  50% { transform: translateY(0) rotateY(0deg) rotateX(0deg); }
  75% { transform: translateY(-5px) rotateY(-2deg) rotateX(-1deg); }
}

@keyframes star-twinkle {
  0%, 100% { opacity: 0.3; transform: scale(1); }
  50% { opacity: 1; transform: scale(1.2); }
}

@keyframes nebula-drift {
  0%, 100% { transform: translateX(0) translateY(0) rotate(0deg); }
  33% { transform: translateX(20px) translateY(-10px) rotate(120deg); }
  66% { transform: translateX(-15px) translateY(15px) rotate(240deg); }
}

@keyframes cosmic-drift {
  0% { transform: translateY(100vh) translateX(0); opacity: 0; }
  10% { opacity: 1; }
  90% { opacity: 1; }
  100% { transform: translateY(-20px) translateX(50px); opacity: 0; }
}

@keyframes danger-pulse {
  0%, 100% { opacity: 1; box-shadow: 0 0 10px currentColor; }
  50% { opacity: 0.7; box-shadow: 0 0 20px currentColor; }
}

@keyframes visor-scan {
  0%, 100% { transform: translateX(-100%); }
  50% { transform: translateX(100%); }
}

@keyframes eye-threat-glow {
  0% { box-shadow: 0 0 15px #ff0000; }
  100% { box-shadow: 0 0 25px #ff0000, 0 0 35px #ff0000; }
}

@keyframes scanner-pulse {
  0%, 100% { transform: translate(-50%, -50%) scale(1); opacity: 1; }
  50% { transform: translate(-50%, -50%) scale(1.5); opacity: 0.7; }
}

@keyframes core-rotation {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

@keyframes core-pulse-danger {
  0%, 100% { opacity: 0.8; transform: translate(-50%, -50%) scale(1); }
  50% { opacity: 1; transform: translate(-50%, -50%) scale(1.1); }
}

@keyframes arm-servo-left {
  0%, 100% { transform: rotate(-15deg); }
  50% { transform: rotate(-25deg); }
}

@keyframes arm-servo-right {
  0%, 100% { transform: rotate(15deg); }
  50% { transform: rotate(25deg); }
}

@keyframes field-pulse {
  0%, 100% { opacity: 0.2; transform: translate(-50%, -50%) scale(1); }
  50% { opacity: 0.6; transform: translate(-50%, -50%) scale(1.1); }
}

@keyframes data-float {
  0%, 100% { transform: translateY(0) translateX(0); opacity: 0.6; }
  50% { transform: translateY(-15px) translateX(10px); opacity: 1; }
}

@keyframes data-pulse {
  0%, 100% { opacity: 0.6; transform: scale(1); }
  50% { opacity: 1; transform: scale(1.3); }
}

@keyframes threat-blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.7; }
}

/* Responsive */
@media (max-width: 768px) {
  .optimus-robot-container {
    max-width: 400px;
    padding: 1rem;
  }
  
  .optimus-robot {
    transform: scale(0.85);
  }
  
  .robot-name {
    font-size: 1rem;
  }
  
  .info-text {
    font-size: 0.9rem;
  }
  
  .system-stats {
    flex-direction: column;
    gap: 0.5rem;
  }
}

@media (max-width: 480px) {
  .optimus-robot {
    transform: scale(0.7);
  }
  
  .robot-header {
    flex-direction: column;
    gap: 1rem;
  }
  
  .capabilities {
    flex-direction: column;
    align-items: center;
  }
  
  .skill-tag {
    width: 100%;
    text-align: center;
    max-width: 200px;
  }
}
</style> 