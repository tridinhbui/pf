<template>
  <div class="robot-container">
    <!-- Robot Status Panel -->
    <div class="robot-status-panel">
      <div class="status-header">
        <div class="status-indicator" :class="{ 'active': isActive }"></div>
        <span class="status-text">{{ isActive ? 'NEXBOT ONLINE' : 'NEXBOT STANDBY' }}</span>
      </div>
      <button class="activate-btn" @click="toggleRobot" :class="{ 'active': isActive }">
        {{ isActive ? 'DEACTIVATE' : 'ACTIVATE NEXBOT' }}
      </button>
    </div>

    <!-- Main Robot Display -->
    <div class="robot-display" :class="{ 'robot-active': isActive }">
      <!-- Holographic Grid -->
      <div class="holographic-grid">
        <div class="grid-line" v-for="n in 15" :key="`h-${n}`" :style="{ top: `${n * 6.67}%` }"></div>
        <div class="grid-line vertical" v-for="n in 15" :key="`v-${n}`" :style="{ left: `${n * 6.67}%` }"></div>
      </div>

      <!-- Energy Rings -->
      <div class="energy-rings">
        <div class="energy-ring" v-for="n in 4" :key="`ring-${n}`" :style="{ animationDelay: `${n * 0.5}s` }"></div>
      </div>

      <!-- Enhanced 3D Robot -->
      <div class="css-robot" :class="{ 'active': isActive }">
        <!-- Robot Head -->
        <div class="robot-head">
          <!-- Multi-layer 3D Head Structure -->
          <div class="head-shell">
            <div class="head-front"></div>
            <div class="head-back"></div>
            <div class="head-left"></div>
            <div class="head-right"></div>
            <div class="head-top"></div>
            <div class="head-bottom"></div>
          </div>
          
          <!-- Advanced Head Details -->
          <div class="head-visor">
            <div class="visor-reflection"></div>
            <div class="visor-scanner"></div>
          </div>
          
          <div class="head-panels">
            <div class="panel panel-left">
              <div class="panel-line" v-for="n in 3" :key="n"></div>
            </div>
            <div class="panel panel-right">
              <div class="panel-line" v-for="n in 3" :key="n"></div>
            </div>
          </div>
          
          <!-- Enhanced Antenna System -->
          <div class="antenna-system">
            <div class="antenna-mount"></div>
            <div class="antenna-main">
              <div class="antenna-segment" v-for="n in 4" :key="n" :style="{ '--delay': n * 0.2 + 's' }"></div>
            </div>
            <div class="signal-array">
              <div class="signal-ring" v-for="n in 5" :key="n" :style="{ '--ring-delay': n * 0.4 + 's' }"></div>
            </div>
            <div class="energy-orb"></div>
          </div>
          
          <!-- Advanced Eyes -->
          <div class="eye-system">
            <div class="eye-assembly left-eye">
              <div class="eye-housing"></div>
              <div class="eye-lens">
                <div class="lens-layer" v-for="n in 3" :key="n"></div>
              </div>
              <div class="pupil-core">
                <div class="pupil-inner"></div>
                <div class="scanning-beam"></div>
              </div>
              <div class="eye-glow-outer"></div>
              <div class="focus-ring"></div>
            </div>
            <div class="eye-assembly right-eye">
              <div class="eye-housing"></div>
              <div class="eye-lens">
                <div class="lens-layer" v-for="n in 3" :key="n"></div>
              </div>
              <div class="pupil-core">
                <div class="pupil-inner"></div>
                <div class="scanning-beam"></div>
              </div>
              <div class="eye-glow-outer"></div>
              <div class="focus-ring"></div>
            </div>
          </div>
          
          <!-- Advanced Mouth System -->
          <div class="mouth-system">
            <div class="mouth-housing"></div>
            <div class="voice-processor">
              <div class="voice-bar" v-for="n in 7" :key="n" :style="{ '--bar-delay': n * 0.1 + 's' }"></div>
            </div>
            <div class="sound-waves">
              <div class="wave-ring" v-for="n in 4" :key="n"></div>
            </div>
          </div>
          
          <!-- Head Status Lights -->
          <div class="status-lights">
            <div class="status-light" v-for="n in 6" :key="n" :class="['light-' + n]"></div>
          </div>
        </div>

        <!-- Robot Body -->
        <div class="robot-body">
          <div class="body-core"></div>
          <div class="chest-panel">
            <div class="power-indicator"></div>
            <div class="data-lines">
              <div class="data-line" v-for="n in 5" :key="n"></div>
            </div>
          </div>
          
          <!-- Arms -->
          <div class="arm left-arm">
            <div class="shoulder"></div>
            <div class="upper-arm"></div>
            <div class="elbow"></div>
            <div class="forearm"></div>
            <div class="hand">
              <div class="finger" v-for="n in 3" :key="n"></div>
            </div>
          </div>
          
          <div class="arm right-arm">
            <div class="shoulder"></div>
            <div class="upper-arm"></div>
            <div class="elbow"></div>
            <div class="forearm"></div>
            <div class="hand">
              <div class="finger" v-for="n in 3" :key="n"></div>
            </div>
          </div>
        </div>

        <!-- Robot Legs -->
        <div class="robot-legs">
          <div class="leg left-leg">
            <div class="thigh"></div>
            <div class="knee"></div>
            <div class="shin"></div>
            <div class="foot"></div>
          </div>
          <div class="leg right-leg">
            <div class="thigh"></div>
            <div class="knee"></div>
            <div class="shin"></div>
            <div class="foot"></div>
          </div>
        </div>

        <!-- Jetpack -->
        <div class="jetpack">
          <div class="jetpack-core"></div>
          <div class="thruster left-thruster">
            <div class="flame"></div>
          </div>
          <div class="thruster right-thruster">
            <div class="flame"></div>
          </div>
        </div>
      </div>

      <!-- Scanning Lines -->
      <div class="scanning-lines" v-if="isActive">
        <div class="scan-line" v-for="n in 3" :key="n" :style="{ animationDelay: `${n * 0.8}s` }"></div>
      </div>

      <!-- Data Streams -->
      <div class="data-streams" v-if="isActive">
        <div class="data-stream" v-for="n in 6" :key="n">
          <div class="data-bit" v-for="m in 8" :key="m"></div>
        </div>
      </div>
    </div>

    <!-- Robot Info Panel -->
    <div class="robot-info-panel" v-if="isActive">
      <div class="info-item">
        <span class="label">STATUS:</span>
        <span class="value">OPERATIONAL</span>
      </div>
      <div class="info-item">
        <span class="label">POWER:</span>
        <span class="value">{{ power }}%</span>
      </div>
      <div class="info-item">
        <span class="label">MODE:</span>
        <span class="value">{{ robotMode }}</span>
      </div>
    </div>

    <!-- Robot Dialogue System -->
    <div class="robot-dialogue" v-if="isActive">
      <div class="dialogue-bubble" :class="{ 'visible': currentMessage }">
        <div class="message-text">{{ currentMessage }}</div>
        <div class="typing-indicator" v-if="isTyping">
          <span></span>
          <span></span>
          <span></span>
        </div>
      </div>
      <div class="metrics-display">
        <div class="metric" v-for="metric in currentMetrics" :key="metric.label">
          <span class="metric-label">{{ metric.label }}:</span>
          <span class="metric-value">{{ metric.value }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

const isActive = ref(false)
const power = ref(100)
const robotMode = ref('STANDBY')
const currentMessage = ref('')
const isTyping = ref(false)
const currentMetrics = ref([])

const modes = ['STANDBY', 'SCANNING', 'PROCESSING', 'ASSISTANT', 'PATROL']

const meaningfulMessages = [
  {
    text: "Hello! I'm NEXBOT. Tri has built 5 ventures that impacted 350+ lives and reached 12K+ users.",
    metrics: [
      { label: "Ventures Founded", value: "5" },
      { label: "Lives Impacted", value: "350+" },
      { label: "Total Users", value: "12K+" }
    ]
  },
  {
    text: "Analyzing Tri's financial expertise: Successfully managed $350M in real estate assets and mitigated $1.5M downside risk.",
    metrics: [
      { label: "Assets Managed", value: "$350M" },
      { label: "Risk Mitigated", value: "$1.5M" },
      { label: "Sharpe Ratio", value: "3.1" }
    ]
  },
  {
    text: "Educational impact report: Pathwise achieved 71% internship success rate. YoungPreneur Academy trained 220 students.",
    metrics: [
      { label: "Success Rate", value: "71%" },
      { label: "Students Trained", value: "220" },
      { label: "Prize Pools", value: "$35K" }
    ]
  },
  {
    text: "FinBud AI performance: 12,000 beta users with 87% Day-30 retention and 3.7 daily sessions per user.",
    metrics: [
      { label: "Beta Users", value: "12K" },
      { label: "Day-30 Retention", value: "87%" },
      { label: "Daily Sessions", value: "3.7" }
    ]
  },
  {
    text: "Corporate experience: $230K scholarship recipient, worked at Deloitte, Blackstone, reduced operational risk by 20%.",
    metrics: [
      { label: "Scholarship Value", value: "$230K" },
      { label: "Op Risk Reduction", value: "20%" },
      { label: "Dean's List", value: "6/6 semesters" }
    ]
  },
  {
    text: "Innovation mindset: Built microservices with 9 modular lambdas, mentored 300+ hours, placed alumni at top firms.",
    metrics: [
      { label: "Mentoring Hours", value: "300+" },
      { label: "Microservices", value: "9 modules" },
      { label: "Top Firm Placements", value: "Multiple" }
    ]
  }
]

const toggleRobot = () => {
  isActive.value = !isActive.value
  if (isActive.value) {
    animateRobotBehavior()
    startDialogueSystem()
  } else {
    robotMode.value = 'STANDBY'
    currentMessage.value = ''
    currentMetrics.value = []
  }
}

const typeMessage = async (message: string) => {
  isTyping.value = true
  currentMessage.value = ''
  
  await new Promise(resolve => setTimeout(resolve, 1000))
  
  isTyping.value = false
  
  for (let i = 0; i <= message.length; i++) {
    currentMessage.value = message.slice(0, i)
    await new Promise(resolve => setTimeout(resolve, 50))
  }
}

const startDialogueSystem = () => {
  // Show first message immediately
  setTimeout(async () => {
    const firstMessage = meaningfulMessages[0]
    await typeMessage(firstMessage.text)
    currentMetrics.value = firstMessage.metrics
  }, 2000)
  
  // Cycle through messages
  let messageIndex = 1
  setInterval(async () => {
    if (isActive.value && messageIndex < meaningfulMessages.length) {
      const message = meaningfulMessages[messageIndex]
      await typeMessage(message.text)
      currentMetrics.value = message.metrics
      messageIndex = (messageIndex + 1) % meaningfulMessages.length
    }
  }, 8000)
}

const animateRobotBehavior = () => {
  setInterval(() => {
    if (isActive.value) {
      robotMode.value = modes[Math.floor(Math.random() * modes.length)]
      
      // Add random robot movements
      const robot = document.querySelector('.css-robot')
      if (robot) {
        const randomMove = Math.random()
        if (randomMove < 0.2) {
          robot.classList.add('lean-left')
          setTimeout(() => robot.classList.remove('lean-left'), 2000)
        } else if (randomMove < 0.4) {
          robot.classList.add('lean-right')
          setTimeout(() => robot.classList.remove('lean-right'), 2000)
        } else if (randomMove < 0.6) {
          robot.classList.add('look-around')
          setTimeout(() => robot.classList.remove('look-around'), 3000)
        }
      }
    }
  }, 4000)
}

// Auto attention-grabbing pulse
onMounted(() => {
  setTimeout(() => {
    if (!isActive.value) {
      const panel = document.querySelector('.robot-status-panel')
      panel?.classList.add('attention-pulse')
      setTimeout(() => {
        panel?.classList.remove('attention-pulse')
      }, 3000)
    }
  }, 3000)
  
  // Power level animation
  const updatePower = () => {
    if (isActive.value) {
      power.value = Math.max(85, Math.min(100, power.value + (Math.random() - 0.5) * 5))
    }
  }
  setInterval(updatePower, 2000)
})
</script>

<style scoped>
.robot-container {
  position: relative;
  width: 100%;
  max-width: 500px;
  margin: 0 auto;
  text-align: center;
}

/* Status Panel */
.robot-status-panel {
  background: rgba(0, 0, 0, 0.9);
  border: 1px solid rgba(100, 200, 255, 0.3);
  border-radius: 15px;
  padding: 1.5rem;
  margin-bottom: 2rem;
  backdrop-filter: blur(10px);
  box-shadow: 0 0 30px rgba(100, 200, 255, 0.2);
}

.robot-status-panel.attention-pulse {
  animation: attention-pulse 3s ease-in-out;
}

@keyframes attention-pulse {
  0%, 100% { transform: scale(1); box-shadow: 0 0 30px rgba(100, 200, 255, 0.2); }
  50% { transform: scale(1.02); box-shadow: 0 0 50px rgba(100, 200, 255, 0.4); }
}

.status-header {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.status-indicator {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: #666666;
  transition: all 0.3s ease;
  box-shadow: 0 0 10px rgba(102, 102, 102, 0.5);
}

.status-indicator.active {
  background: #00ff88;
  box-shadow: 0 0 20px rgba(0, 255, 136, 0.8);
  animation: status-pulse 2s infinite;
}

@keyframes status-pulse {
  0%, 100% { transform: scale(1); opacity: 1; }
  50% { transform: scale(1.2); opacity: 0.8; }
}

.status-text {
  color: #ffffff;
  font-family: 'Courier New', monospace;
  font-weight: bold;
  font-size: 0.875rem;
  letter-spacing: 0.1em;
}

.activate-btn {
  background: linear-gradient(45deg, #333333, #555555);
  color: #ffffff;
  border: 1px solid rgba(100, 200, 255, 0.3);
  border-radius: 10px;
  padding: 1rem 2rem;
  font-family: 'Courier New', monospace;
  font-weight: bold;
  font-size: 0.875rem;
  letter-spacing: 0.05em;
  cursor: pointer;
  transition: all 0.3s ease;
  text-transform: uppercase;
}

.activate-btn:hover {
  background: linear-gradient(45deg, #555555, #777777);
  transform: translateY(-2px);
  box-shadow: 0 5px 20px rgba(100, 200, 255, 0.3);
}

.activate-btn.active {
  background: linear-gradient(45deg, #00ff88, #00cc66);
  border-color: #00ff88;
  box-shadow: 0 0 25px rgba(0, 255, 136, 0.5);
}

/* Robot Display */
.robot-display {
  position: relative;
  width: 400px;
  height: 500px;
  margin: 0 auto;
  background: radial-gradient(circle at center, rgba(40, 0, 0, 0.3), rgba(0, 0, 0, 0.9));
  border: 2px solid rgba(255, 0, 64, 0.3);
  border-radius: 20px;
  overflow: hidden;
  transition: all 0.5s ease;
  box-shadow: 
    0 0 30px rgba(255, 0, 64, 0.2),
    inset 0 0 50px rgba(255, 255, 255, 0.05);
}

.robot-display.robot-active {
  border-color: rgba(255, 0, 64, 0.7);
  box-shadow: 
    0 0 50px rgba(255, 0, 64, 0.5),
    0 0 100px rgba(255, 0, 64, 0.3),
    inset 0 0 30px rgba(255, 255, 255, 0.1);
  background: radial-gradient(circle at center, rgba(60, 0, 0, 0.5), rgba(20, 0, 0, 0.95));
}

/* Holographic Grid */
.holographic-grid {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: 0.3;
}

.grid-line {
  position: absolute;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), rgba(255, 0, 64, 0.4), rgba(255, 255, 255, 0.3), transparent);
  height: 1px;
  width: 100%;
  animation: grid-pulse 4s linear infinite;
}

.grid-line.vertical {
  width: 1px;
  height: 100%;
  background: linear-gradient(0deg, transparent, rgba(255, 255, 255, 0.3), rgba(255, 0, 64, 0.4), rgba(255, 255, 255, 0.3), transparent);
}

@keyframes grid-pulse {
  0%, 100% { opacity: 0.2; }
  50% { opacity: 0.6; }
}

/* Energy Rings */
.energy-rings {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.energy-ring {
  position: absolute;
  width: 300px;
  height: 300px;
  border: 2px solid rgba(255, 0, 64, 0.4);
  border-radius: 50%;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  animation: energy-expand 3s ease-out infinite;
  box-shadow: 
    0 0 20px rgba(255, 0, 64, 0.3),
    inset 0 0 20px rgba(255, 255, 255, 0.1);
}

@keyframes energy-expand {
  0% { width: 50px; height: 50px; opacity: 1; }
  100% { width: 400px; height: 400px; opacity: 0; }
}

/* Robot Movement Animations */
.css-robot.lean-left {
  animation: leanLeft 2s ease-in-out;
}

.css-robot.lean-right {
  animation: leanRight 2s ease-in-out;
}

.css-robot.look-around {
  animation: lookAround 3s ease-in-out;
}

@keyframes leanLeft {
  0%, 100% { transform: translate(-50%, -50%) rotate(0deg); }
  50% { transform: translate(-50%, -50%) rotate(-5deg) translateX(-10px); }
}

@keyframes leanRight {
  0%, 100% { transform: translate(-50%, -50%) rotate(0deg); }
  50% { transform: translate(-50%, -50%) rotate(5deg) translateX(10px); }
}

@keyframes lookAround {
  0%, 100% { transform: translate(-50%, -50%) rotate(0deg); }
  25% { transform: translate(-50%, -50%) rotate(-3deg); }
  75% { transform: translate(-50%, -50%) rotate(3deg); }
}

/* CSS Robot */
.css-robot {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  transition: all 0.5s ease;
}

.css-robot.active {
  animation: robot-float 4s ease-in-out infinite;
}

@keyframes robot-float {
  0%, 100% { transform: translate(-50%, -50%) translateY(0); }
  50% { transform: translate(-50%, -50%) translateY(-10px); }
}

/* Enhanced 3D Robot Head */
.robot-head {
  position: relative;
  width: 120px;
  height: 100px;
  margin: 0 auto 15px;
  transform-style: preserve-3d;
  animation: head-ultra-rotate 12s linear infinite;
  perspective: 1000px;
}

@keyframes head-ultra-rotate {
  0% { transform: rotateY(0deg) rotateX(0deg) rotateZ(0deg); }
  20% { transform: rotateY(72deg) rotateX(10deg) rotateZ(5deg); }
  40% { transform: rotateY(144deg) rotateX(-5deg) rotateZ(-3deg); }
  60% { transform: rotateY(216deg) rotateX(15deg) rotateZ(8deg); }
  80% { transform: rotateY(288deg) rotateX(-10deg) rotateZ(-5deg); }
  100% { transform: rotateY(360deg) rotateX(0deg) rotateZ(0deg); }
}

/* Multi-Layer Head Shell */
.head-shell {
  position: relative;
  width: 100%;
  height: 100%;
  transform-style: preserve-3d;
}

.head-front {
  position: absolute;
  width: 100px;
  height: 80px;
  background: linear-gradient(135deg, #1a1a1a, #ffffff, #2a2a2a, #ff0040);
  border-radius: 20px;
  border: 3px solid #ff0040;
  transform: translateZ(25px);
  box-shadow: 
    inset 0 0 30px rgba(255, 0, 64, 0.3),
    0 10px 30px rgba(0, 0, 0, 0.7),
    0 0 50px rgba(255, 0, 64, 0.6),
    0 0 100px rgba(255, 255, 255, 0.2);
}

.head-back {
  position: absolute;
  width: 95px;
  height: 75px;
  background: linear-gradient(135deg, #000000, #2a2a2a, #ff0040);
  border-radius: 18px;
  transform: translateZ(-25px);
  left: 2.5px;
  top: 2.5px;
  opacity: 0.9;
  border: 2px solid #ff0040;
}

.head-left, .head-right {
  position: absolute;
  width: 50px;
  height: 80px;
  background: linear-gradient(90deg, #1a1a1a, #ffffff, #2a2a2a);
  border-radius: 15px;
  top: 0;
  border: 2px solid #ff0040;
}

.head-left {
  left: -15px;
  transform: rotateY(-90deg) translateZ(25px);
}

.head-right {
  right: -15px;
  transform: rotateY(90deg) translateZ(25px);
}

.head-top {
  position: absolute;
  width: 100px;
  height: 50px;
  background: linear-gradient(0deg, #999999, #bbbbbb);
  border-radius: 20px 20px 10px 10px;
  transform: rotateX(90deg) translateZ(25px);
  top: -15px;
}

.head-bottom {
  position: absolute;
  width: 100px;
  height: 50px;
  background: linear-gradient(0deg, #666666, #888888);
  border-radius: 10px 10px 20px 20px;
  transform: rotateX(-90deg) translateZ(25px);
  bottom: -15px;
}

/* Advanced Head Visor */
.head-visor {
  position: absolute;
  top: 15px;
  left: 10px;
  width: 80px;
  height: 30px;
  background: linear-gradient(45deg, rgba(100, 200, 255, 0.3), rgba(0, 255, 136, 0.3));
  border-radius: 15px;
  transform: translateZ(30px);
  backdrop-filter: blur(2px);
  border: 1px solid rgba(100, 200, 255, 0.5);
  animation: visor-scan 3s ease-in-out infinite;
}

@keyframes visor-scan {
  0%, 100% { box-shadow: 0 0 15px rgba(100, 200, 255, 0.5); }
  50% { box-shadow: 0 0 30px rgba(0, 255, 136, 0.8); }
}

.visor-reflection {
  position: absolute;
  top: 2px;
  left: 2px;
  width: 76px;
  height: 10px;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.6), transparent);
  border-radius: 10px;
  animation: reflection-sweep 4s ease-in-out infinite;
}

@keyframes reflection-sweep {
  0% { transform: translateX(-100%); }
  100% { transform: translateX(100%); }
}

.visor-scanner {
  position: absolute;
  bottom: 5px;
  left: 20px;
  width: 40px;
  height: 2px;
  background: #00ff88;
  box-shadow: 0 0 10px #00ff88;
  animation: scanner-move 2s ease-in-out infinite alternate;
}

@keyframes scanner-move {
  0% { transform: translateX(-20px); }
  100% { transform: translateX(20px); }
}

@keyframes head-3d-rotate {
  0% { transform: rotateY(0deg) rotateX(0deg); }
  25% { transform: rotateY(15deg) rotateX(5deg); }
  50% { transform: rotateY(0deg) rotateX(10deg); }
  75% { transform: rotateY(-15deg) rotateX(5deg); }
  100% { transform: rotateY(0deg) rotateX(0deg); }
}

.head-core {
  width: 80px;
  height: 60px;
  background: linear-gradient(135deg, #888888, #aaaaaa, #666666);
  border-radius: 15px;
  border: 2px solid #555555;
  position: relative;
  box-shadow: 
    inset 0 0 20px rgba(0, 0, 0, 0.3),
    0 5px 15px rgba(0, 0, 0, 0.4),
    0 0 30px rgba(100, 200, 255, 0.2);
  transform: translateZ(10px);
}

.head-depth-layer {
  position: absolute;
  width: 76px;
  height: 56px;
  background: linear-gradient(135deg, #666666, #888888);
  border-radius: 13px;
  top: 2px;
  left: 2px;
  transform: translateZ(-5px);
  opacity: 0.7;
}

.head-side-panel {
  position: absolute;
  width: 15px;
  height: 50px;
  background: linear-gradient(90deg, #555555, #777777);
  border-radius: 5px;
  top: 5px;
  border: 1px solid #444444;
  transform: translateZ(8px);
}

.head-side-panel.left-side {
  left: -10px;
  transform: translateZ(8px) rotateY(-30deg);
}

.head-side-panel.right-side {
  right: -10px;
  transform: translateZ(8px) rotateY(30deg);
}

.antenna {
  position: absolute;
  top: -15px;
  left: 50%;
  transform: translateX(-50%) translateZ(15px);
  width: 4px;
  height: 20px;
  background: linear-gradient(0deg, #888888, #aaaaaa);
  border-radius: 2px;
  animation: antenna-pulse 3s ease-in-out infinite;
  transform-style: preserve-3d;
}

.antenna-base {
  width: 8px;
  height: 6px;
  background: radial-gradient(circle, #aaaaaa, #666666);
  border-radius: 50%;
  position: absolute;
  bottom: -3px;
  left: -2px;
  transform: translateZ(2px);
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.3);
}

.antenna-segment {
  width: 3px;
  height: 8px;
  background: linear-gradient(0deg, #999999, #bbbbbb);
  border-radius: 1px;
  position: absolute;
  top: 6px;
  left: 0.5px;
  transform: translateZ(3px);
  animation: segment-glow 2s ease-in-out infinite;
}

.antenna-segment:nth-child(3) {
  top: 2px;
  background: linear-gradient(0deg, #777777, #999999);
}

@keyframes segment-glow {
  0%, 100% { box-shadow: 0 0 5px rgba(100, 200, 255, 0.3); }
  50% { box-shadow: 0 0 15px rgba(100, 200, 255, 0.8); }
}

.signal-pulse {
  position: absolute;
  top: -5px;
  left: -8px;
  width: 20px;
  height: 20px;
  border: 2px solid rgba(100, 200, 255, 0.6);
  border-radius: 50%;
  animation: signal-expand 2s ease-out infinite;
  transform: translateZ(5px);
}

@keyframes signal-expand {
  0% { width: 5px; height: 5px; opacity: 1; left: -1px; top: -1px; }
  100% { width: 30px; height: 30px; opacity: 0; left: -13px; top: -13px; }
}

.antenna-tip {
  position: absolute;
  top: -8px;
  left: 50%;
  transform: translateX(-50%);
  width: 12px;
  height: 12px;
  background: radial-gradient(circle, #00ff88, #00cc66);
  border-radius: 50%;
  box-shadow: 0 0 15px rgba(0, 255, 136, 0.8);
  animation: tip-glow 2s ease-in-out infinite alternate;
}

@keyframes antenna-pulse {
  0%, 100% { transform: translateX(-50%) scaleY(1); }
  50% { transform: translateX(-50%) scaleY(1.1); }
}

@keyframes tip-glow {
  0% { box-shadow: 0 0 15px rgba(0, 255, 136, 0.8); }
  100% { box-shadow: 0 0 25px rgba(0, 255, 136, 1), 0 0 35px rgba(0, 255, 136, 0.5); }
}

/* Eyes */
.eyes {
  position: absolute;
  top: 15px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 20px;
}

.eye {
  position: relative;
  width: 20px;
  height: 20px;
  background: #222222;
  border-radius: 50%;
  border: 2px solid #444444;
}

.pupil {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 12px;
  height: 12px;
  background: radial-gradient(circle at 30% 30%, #00ff88, #00cc66);
  border-radius: 50%;
  animation: eye-blink 4s infinite;
}

.eye-glow {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 25px;
  height: 25px;
  background: radial-gradient(circle, rgba(0, 255, 136, 0.3), transparent);
  border-radius: 50%;
  animation: glow-pulse 3s ease-in-out infinite;
}

@keyframes eye-blink {
  0%, 90%, 100% { transform: translate(-50%, -50%) scaleY(1); }
  95% { transform: translate(-50%, -50%) scaleY(0.1); }
}

@keyframes glow-pulse {
  0%, 100% { opacity: 0.5; transform: translate(-50%, -50%) scale(1); }
  50% { opacity: 1; transform: translate(-50%, -50%) scale(1.2); }
}

/* Mouth */
.mouth {
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  gap: 2px;
}

.mouth-line {
  width: 30px;
  height: 2px;
  background: #00ff88;
  border-radius: 1px;
  animation: mouth-talk 2s ease-in-out infinite;
  opacity: 0.7;
}

.mouth-line:nth-child(2) { animation-delay: 0.3s; }
.mouth-line:nth-child(3) { animation-delay: 0.6s; }

@keyframes mouth-talk {
  0%, 100% { width: 30px; opacity: 0.7; }
  50% { width: 20px; opacity: 1; }
}

/* Robot Body */
.robot-body {
  position: relative;
  width: 120px;
  height: 140px;
  margin: 0 auto 15px;
}

.body-core {
  width: 100px;
  height: 120px;
  background: linear-gradient(135deg, #777777, #999999, #777777);
  border-radius: 20px;
  border: 2px solid #555555;
  margin: 0 auto;
  box-shadow: inset 0 0 30px rgba(0, 0, 0, 0.3);
}

.chest-panel {
  position: absolute;
  top: 20px;
  left: 50%;
  transform: translateX(-50%);
  width: 60px;
  height: 80px;
  background: rgba(0, 0, 0, 0.5);
  border-radius: 10px;
  border: 1px solid #00ff88;
  padding: 10px;
}

.power-indicator {
  width: 100%;
  height: 20px;
  background: linear-gradient(90deg, #00ff88, #00cc66);
  border-radius: 5px;
  margin-bottom: 10px;
  animation: power-pulse 2s ease-in-out infinite;
}

@keyframes power-pulse {
  0%, 100% { box-shadow: 0 0 10px rgba(0, 255, 136, 0.5); }
  50% { box-shadow: 0 0 20px rgba(0, 255, 136, 0.8); }
}

.data-lines {
  display: flex;
  flex-direction: column;
  gap: 3px;
}

.data-line {
  height: 2px;
  background: rgba(0, 255, 136, 0.6);
  border-radius: 1px;
  animation: data-flow 1.5s ease-in-out infinite;
}

.data-line:nth-child(1) { width: 80%; animation-delay: 0s; }
.data-line:nth-child(2) { width: 60%; animation-delay: 0.3s; }
.data-line:nth-child(3) { width: 90%; animation-delay: 0.6s; }
.data-line:nth-child(4) { width: 70%; animation-delay: 0.9s; }
.data-line:nth-child(5) { width: 85%; animation-delay: 1.2s; }

@keyframes data-flow {
  0%, 100% { opacity: 0.6; transform: scaleX(1); }
  50% { opacity: 1; transform: scaleX(1.1); }
}

/* Arms */
.arm {
  position: absolute;
  top: 20px;
  animation: arm-wave 6s ease-in-out infinite;
}

.left-arm {
  left: -40px;
  animation-delay: 0s;
}

.right-arm {
  right: -40px;
  animation-delay: 3s;
}

@keyframes arm-wave {
  0%, 80%, 100% { transform: rotate(0deg); }
  10%, 70% { transform: rotate(-15deg); }
  40% { transform: rotate(15deg); }
}

.shoulder {
  width: 25px;
  height: 25px;
  background: #666666;
  border-radius: 50%;
  border: 2px solid #444444;
  margin-bottom: 5px;
}

.upper-arm, .forearm {
  width: 15px;
  height: 30px;
  background: linear-gradient(135deg, #777777, #555555);
  border-radius: 7px;
  border: 1px solid #333333;
  margin-bottom: 5px;
}

.elbow {
  width: 20px;
  height: 15px;
  background: #666666;
  border-radius: 50%;
  border: 1px solid #444444;
  margin-bottom: 5px;
}

.hand {
  width: 20px;
  height: 15px;
  background: #777777;
  border-radius: 7px;
  border: 1px solid #555555;
  display: flex;
  justify-content: space-around;
  align-items: flex-end;
  padding: 2px;
}

.finger {
  width: 3px;
  height: 8px;
  background: #888888;
  border-radius: 1px;
  animation: finger-wiggle 4s ease-in-out infinite;
}

.finger:nth-child(1) { animation-delay: 0s; }
.finger:nth-child(2) { animation-delay: 0.5s; }
.finger:nth-child(3) { animation-delay: 1s; }

@keyframes finger-wiggle {
  0%, 90%, 100% { transform: scaleY(1); }
  45% { transform: scaleY(1.2); }
}

/* Legs */
.robot-legs {
  display: flex;
  justify-content: center;
  gap: 20px;
}

.leg {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.thigh {
  width: 20px;
  height: 40px;
  background: linear-gradient(135deg, #777777, #555555);
  border-radius: 10px;
  border: 1px solid #333333;
  margin-bottom: 5px;
}

.knee {
  width: 25px;
  height: 15px;
  background: #666666;
  border-radius: 50%;
  border: 1px solid #444444;
  margin-bottom: 5px;
}

.shin {
  width: 18px;
  height: 35px;
  background: linear-gradient(135deg, #777777, #555555);
  border-radius: 9px;
  border: 1px solid #333333;
  margin-bottom: 5px;
}

.foot {
  width: 30px;
  height: 12px;
  background: #888888;
  border-radius: 6px;
  border: 1px solid #666666;
}

/* Jetpack */
.jetpack {
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  z-index: -1;
}

.jetpack-core {
  width: 60px;
  height: 80px;
  background: linear-gradient(135deg, #444444, #666666);
  border-radius: 15px;
  border: 2px solid #333333;
  margin-bottom: 10px;
}

.thruster {
  position: absolute;
  bottom: -15px;
  width: 20px;
  height: 25px;
  background: #555555;
  border-radius: 0 0 10px 10px;
}

.left-thruster { left: 5px; }
.right-thruster { right: 5px; }

.flame {
  position: absolute;
  bottom: -20px;
  left: 50%;
  transform: translateX(-50%);
  width: 12px;
  height: 25px;
  background: linear-gradient(0deg, transparent, #ff6600, #ffaa00);
  border-radius: 0 0 50% 50%;
  animation: flame-flicker 0.3s ease-in-out infinite alternate;
}

@keyframes flame-flicker {
  0% { transform: translateX(-50%) scaleY(1) scaleX(1); }
  100% { transform: translateX(-50%) scaleY(1.2) scaleX(0.8); }
}

/* Scanning Lines */
.scanning-lines {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
}

.scan-line {
  position: absolute;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, transparent, rgba(0, 255, 136, 0.8), transparent);
  animation: scan-sweep 3s linear infinite;
}

@keyframes scan-sweep {
  0% { top: 0%; opacity: 0; }
  10% { opacity: 1; }
  90% { opacity: 1; }
  100% { top: 100%; opacity: 0; }
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
  gap: 10px;
  animation: stream-flow 4s linear infinite;
}

.data-stream:nth-child(1) { left: 10%; animation-delay: 0s; }
.data-stream:nth-child(2) { left: 30%; animation-delay: 0.5s; }
.data-stream:nth-child(3) { left: 50%; animation-delay: 1s; }
.data-stream:nth-child(4) { left: 70%; animation-delay: 1.5s; }
.data-stream:nth-child(5) { left: 90%; animation-delay: 2s; }
.data-stream:nth-child(6) { left: 20%; animation-delay: 2.5s; }

.data-bit {
  width: 6px;
  height: 6px;
  background: rgba(0, 255, 136, 0.8);
  border-radius: 50%;
  box-shadow: 0 0 6px rgba(0, 255, 136, 0.6);
}

@keyframes stream-flow {
  0% { transform: translateY(-50px); opacity: 0; }
  10% { opacity: 1; }
  90% { opacity: 1; }
  100% { transform: translateY(550px); opacity: 0; }
}

/* Robot Info Panel */
.robot-info-panel {
  background: rgba(0, 0, 0, 0.9);
  border: 1px solid rgba(0, 255, 136, 0.3);
  border-radius: 10px;
  padding: 1rem;
  margin-top: 2rem;
  font-family: 'Courier New', monospace;
  font-size: 0.875rem;
}

.info-item {
  display: flex;
  justify-content: space-between;
  margin-bottom: 0.5rem;
  color: #ffffff;
}

.label {
  color: rgba(255, 255, 255, 0.7);
}

.value {
  color: #00ff88;
  font-weight: bold;
}

/* Robot Dialogue Styles */
.robot-dialogue {
  margin-top: 2rem;
  padding: 1.5rem;
  background: rgba(0, 0, 0, 0.9);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 15px;
  backdrop-filter: blur(10px);
}

.dialogue-bubble {
  background: rgba(255, 255, 255, 0.05);
  border-left: 4px solid #ffffff;
  padding: 1rem 1.5rem;
  border-radius: 10px;
  margin-bottom: 1rem;
  opacity: 0;
  transform: translateY(10px);
  transition: all 0.3s ease;
}

.dialogue-bubble.visible {
  opacity: 1;
  transform: translateY(0);
}

.message-text {
  color: #ffffff;
  font-family: 'Arial', sans-serif;
  font-size: 0.9rem;
  line-height: 1.5;
  margin-bottom: 0.5rem;
}

.typing-indicator {
  display: flex;
  gap: 4px;
  margin-top: 0.5rem;
}

.typing-indicator span {
  width: 6px;
  height: 6px;
  background: #ffffff;
  border-radius: 50%;
  animation: typing-bounce 1.4s infinite ease-in-out;
}

.typing-indicator span:nth-child(1) { animation-delay: 0s; }
.typing-indicator span:nth-child(2) { animation-delay: 0.2s; }
.typing-indicator span:nth-child(3) { animation-delay: 0.4s; }

@keyframes typing-bounce {
  0%, 60%, 100% { transform: translateY(0); opacity: 0.3; }
  30% { transform: translateY(-8px); opacity: 1; }
}

.metrics-display {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
  gap: 1rem;
  margin-top: 1rem;
}

.metric {
  background: rgba(255, 255, 255, 0.03);
  padding: 0.75rem;
  border-radius: 8px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  text-align: center;
}

.metric-label {
  display: block;
  color: #cccccc;
  font-size: 0.75rem;
  font-weight: 500;
  margin-bottom: 0.25rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.metric-value {
  display: block;
  color: #ffffff;
  font-size: 1.1rem;
  font-weight: bold;
  font-family: 'Courier New', monospace;
}

/* Responsive */
@media (max-width: 768px) {
  .robot-container {
    max-width: 350px;
  }
  
  .robot-display {
    width: 300px;
    height: 400px;
  }
  
  .robot-status-panel {
    padding: 1rem;
  }
  
  .activate-btn {
    padding: 0.75rem 1.5rem;
    font-size: 0.75rem;
  }
  
  .robot-dialogue {
    padding: 1rem;
  }
  
  .metrics-display {
    grid-template-columns: 1fr;
    gap: 0.5rem;
  }
  
  .message-text {
    font-size: 0.8rem;
  }
}
</style> 