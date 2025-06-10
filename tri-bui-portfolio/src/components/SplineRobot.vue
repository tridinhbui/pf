<template>
  <div class="nexbot-container">
    <!-- Header Control Panel -->
    <div class="nexbot-header">
      <div class="system-info">
        <div class="system-badge">
          <span class="system-name">NEXBOT AI</span>
          <span class="system-version">v2.1.4</span>
        </div>
        <div class="status-indicators">
          <div class="indicator" :class="{ 'active': isActive, 'processing': isProcessing }">
            <div class="indicator-dot"></div>
            <span>{{ isActive ? 'ONLINE' : 'OFFLINE' }}</span>
          </div>
          <div class="network-indicator">
            <div class="signal-bars">
              <div class="bar" v-for="n in 4" :key="n" :style="{ animationDelay: n * 0.1 + 's' }"></div>
            </div>
            <span>CONNECTED</span>
          </div>
        </div>
      </div>
      
      <div class="control-panel">
        <button @click="toggleVoice" class="control-btn" :class="{ 'active': voiceEnabled }">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor">
            <polygon v-if="voiceEnabled" points="11 5 6 9 2 9 2 15 6 15 11 19 11 5"></polygon>
            <path v-if="voiceEnabled" d="m19.07 4.93-1.41 1.41A8.5 8.5 0 0 1 19 12a8.5 8.5 0 0 1-1.34 5.66l1.41 1.41A10.48 10.48 0 0 0 21 12a10.48 10.48 0 0 0-1.93-7.07z"></path>
            <polygon v-else points="11 5 6 9 2 9 2 15 6 15 11 19 11 5"></polygon>
            <line v-if="!voiceEnabled" x1="23" y1="9" x2="17" y2="15"></line>
            <line v-if="!voiceEnabled" x1="17" y1="9" x2="23" y2="15"></line>
          </svg>
          <span>{{ voiceEnabled ? 'VOICE' : 'MUTED' }}</span>
        </button>
        
        <button @click="cycleMode" class="control-btn">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor">
            <path d="M3 12a9 9 0 1 0 9-9 9.75 9.75 0 0 0-6.74 2.74L3 8"></path>
            <path d="m3 3 2.5 5H11"></path>
          </svg>
          <span>MODE</span>
        </button>
        
        <button @click="resetSystem" class="control-btn">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor">
            <path d="M21 12a9 9 0 1 1-9-9c2.52 0 4.93 1 6.74 2.74L21 8"></path>
            <path d="M21 3v5h-5"></path>
          </svg>
          <span>RESET</span>
        </button>
      </div>
    </div>

    <!-- Main Display Area -->
    <div class="nexbot-main">
      <!-- Left Side: 3D Robot Display -->
      <div class="robot-display-area">
        <div class="hologram-frame">
          <div class="scan-lines"></div>
          <div class="grid-overlay">
            <div class="grid-line" v-for="n in 8" :key="`h-${n}`"></div>
            <div class="grid-line vertical" v-for="n in 8" :key="`v-${n}`"></div>
          </div>
          
          <!-- Enhanced 3D Robot -->
          <div class="nexbot-3d" :class="{ 'active': isActive, 'processing': isProcessing }">
            <!-- Robot Head with Advanced Features -->
            <div class="robot-head">
              <div class="head-shell">
                <div class="head-surface"></div>
                <div class="head-reflections"></div>
              </div>
              
              <!-- Advanced Eyes with AI Processing -->
              <div class="eye-system">
                <div class="eye left-eye">
                  <div class="eye-lens">
                    <div class="iris" :style="{ backgroundColor: currentModeColor }"></div>
                    <div class="pupil">
                      <div class="scan-beam" v-if="isProcessing"></div>
                    </div>
                  </div>
                  <div class="eye-glow" :style="{ boxShadow: `0 0 20px ${currentModeColor}` }"></div>
                </div>
                <div class="eye right-eye">
                  <div class="eye-lens">
                    <div class="iris" :style="{ backgroundColor: currentModeColor }"></div>
                    <div class="pupil">
                      <div class="scan-beam" v-if="isProcessing"></div>
                    </div>
                  </div>
                  <div class="eye-glow" :style="{ boxShadow: `0 0 20px ${currentModeColor}` }"></div>
                </div>
              </div>
              
              <!-- Neural Network Visualization -->
              <div class="neural-network" v-if="isActive">
                <div class="neural-node" v-for="n in 6" :key="n" :style="{ animationDelay: n * 0.2 + 's' }"></div>
                <div class="neural-connection" v-for="n in 8" :key="n"></div>
              </div>
              
              <!-- Advanced Antenna Array -->
              <div class="antenna-array">
                <div class="antenna primary" :class="{ 'transmitting': isTransmitting }">
                  <div class="antenna-tip"></div>
                  <div class="signal-ring" v-for="n in 3" :key="n"></div>
                </div>
                <div class="antenna secondary" v-for="n in 2" :key="n"></div>
              </div>
            </div>

            <!-- Robot Body with Tech Details -->
            <div class="robot-body">
              <div class="body-core">
                <div class="power-core" :style="{ backgroundColor: currentModeColor }"></div>
                <div class="energy-flow">
                  <div class="flow-particle" v-for="n in 6" :key="n"></div>
                </div>
              </div>
              
              <div class="chest-panel">
                <div class="panel-display">
                  <div class="display-line" v-for="n in 4" :key="n" :style="{ animationDelay: n * 0.1 + 's' }"></div>
                </div>
                <div class="status-lights">
                  <div class="status-light" v-for="n in 8" :key="n" :class="{ 'active': n <= Math.floor(power/12.5) }"></div>
                </div>
              </div>
              
              <!-- Floating Holographic Elements -->
              <div class="holo-elements" v-if="isActive">
                <div class="data-stream" v-for="n in 4" :key="n">
                  <div class="data-bit" v-for="m in 6" :key="m"></div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Right Side: Information Panels -->
      <div class="info-panels">
        <!-- System Status Panel -->
        <div class="panel status-panel">
          <div class="panel-header">
            <h4>SYSTEM STATUS</h4>
            <div class="panel-indicator" :class="systemHealthClass"></div>
          </div>
          <div class="panel-content">
            <div class="status-grid">
              <div class="status-item">
                <span class="label">CPU</span>
                <div class="progress-bar">
                  <div class="progress-fill" :style="{ width: cpuUsage + '%' }"></div>
                </div>
                <span class="value">{{ cpuUsage }}%</span>
              </div>
              <div class="status-item">
                <span class="label">RAM</span>
                <div class="progress-bar">
                  <div class="progress-fill" :style="{ width: ramUsage + '%' }"></div>
                </div>
                <span class="value">{{ ramUsage }}%</span>
              </div>
              <div class="status-item">
                <span class="label">PWR</span>
                <div class="progress-bar">
                  <div class="progress-fill" :style="{ width: power + '%' }"></div>
                </div>
                <span class="value">{{ power }}%</span>
              </div>
              <div class="status-item">
                <span class="label">NET</span>
                <div class="progress-bar">
                  <div class="progress-fill" :style="{ width: networkSpeed + '%' }"></div>
                </div>
                <span class="value">{{ networkSpeed }}%</span>
              </div>
            </div>
            
            <div class="system-mode">
              <span class="mode-label">MODE:</span>
              <span class="mode-value" :style="{ color: currentModeColor }">{{ robotMode }}</span>
            </div>
          </div>
        </div>

        <!-- AI Analytics Panel -->
        <div class="panel analytics-panel">
          <div class="panel-header">
            <h4>AI ANALYTICS</h4>
            <div class="analytics-indicator pulsing"></div>
          </div>
          <div class="panel-content">
            <div class="analytics-grid">
              <div class="metric-card" v-for="metric in aiMetrics" :key="metric.label">
                <div class="metric-icon">{{ metric.icon }}</div>
                <div class="metric-info">
                  <div class="metric-value">{{ metric.value }}</div>
                  <div class="metric-label">{{ metric.label }}</div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Communication Panel -->
        <div class="panel communication-panel" v-if="currentMessage">
          <div class="panel-header">
            <h4>COMMUNICATION</h4>
            <div class="comm-indicator" :class="{ 'transmitting': isTyping }"></div>
          </div>
          <div class="panel-content">
            <div class="message-display">
              <div class="message-avatar">
                <div class="avatar-glow" :style="{ backgroundColor: currentModeColor }"></div>
                <span>AI</span>
              </div>
              <div class="message-content">
                <div class="typing-animation" v-if="isTyping">
                  <div class="typing-dot" v-for="n in 3" :key="n"></div>
                </div>
                <p v-else class="message-text">{{ currentMessage }}</p>
              </div>
            </div>
            
            <div class="response-stats">
              <div class="stat">
                <span class="stat-label">Response Time:</span>
                <span class="stat-value">{{ responseTime }}ms</span>
              </div>
              <div class="stat">
                <span class="stat-label">Confidence:</span>
                <span class="stat-value">{{ confidence }}%</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Performance Metrics Panel -->
        <div class="panel performance-panel">
          <div class="panel-header">
            <h4>PERFORMANCE</h4>
            <div class="perf-indicator optimal"></div>
          </div>
          <div class="panel-content">
            <div class="performance-chart">
              <div class="chart-bars">
                <div class="chart-bar" v-for="value in performanceData" :key="value.id" 
                     :style="{ height: value.height + '%', backgroundColor: currentModeColor }">
                </div>
              </div>
              <div class="chart-labels">
                <span v-for="n in 8" :key="n">{{ n }}h</span>
              </div>
            </div>
            
            <div class="performance-stats">
              <div class="perf-stat">
                <span class="perf-value">{{ totalQueries }}</span>
                <span class="perf-label">Queries Processed</span>
              </div>
              <div class="perf-stat">
                <span class="perf-value">{{ avgResponseTime }}ms</span>
                <span class="perf-label">Avg Response Time</span>
              </div>
              <div class="perf-stat">
                <span class="perf-value">{{ uptime }}</span>
                <span class="perf-label">System Uptime</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Footer Status Bar -->
    <div class="nexbot-footer">
      <div class="footer-stats">
        <div class="stat-item">
          <span class="stat-icon">🚀</span>
          <span class="stat-text">{{ totalInteractions }} interactions</span>
        </div>
        <div class="stat-item">
          <span class="stat-icon">⚡</span>
          <span class="stat-text">{{ Math.round(Date.now() / 1000) }}s uptime</span>
        </div>
        <div class="stat-item">
          <span class="stat-icon">🧠</span>
          <span class="stat-text">Neural Net: Active</span>
        </div>
      </div>
      
      <div class="footer-controls">
        <button @click="exportLogs" class="footer-btn">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor">
            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
            <polyline points="7,10 12,15 17,10"></polyline>
            <line x1="12" y1="15" x2="12" y2="3"></line>
          </svg>
          Export Logs
        </button>
        <button @click="openDiagnostics" class="footer-btn">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor">
            <path d="M14.7 6.3a1 1 0 0 0 0 1.4l1.6 1.6a1 1 0 0 0 1.4 0l3.77-3.77a6 6 0 0 1-7.94 7.94l-6.91 6.91a2.12 2.12 0 0 1-3-3l6.91-6.91a6 6 0 0 1 7.94-7.94l-3.76 3.76z"></path>
          </svg>
          Diagnostics
        </button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

const isActive = ref(true) // Auto-activate
const power = ref(100)
const robotMode = ref('ACTIVE')
const currentMessage = ref('')
const isTyping = ref(false)
const currentMetrics = ref<Array<{label: string, value: string}>>([])
const voiceEnabled = ref(true) // Voice control

// Enhanced system metrics
const isProcessing = ref(false)
const isTransmitting = ref(false)
const cpuUsage = ref(75)
const ramUsage = ref(62)
const networkSpeed = ref(98)
const responseTime = ref(145)
const confidence = ref(97)
const totalQueries = ref(1247)
const avgResponseTime = ref(142)
const uptime = ref('24h 37m')
const totalInteractions = ref(3842)

// Advanced features
const currentModeColor = ref('#00ff88')
const systemHealthClass = ref('optimal')

const modes = ['STANDBY', 'SCANNING', 'PROCESSING', 'ASSISTANT', 'PATROL', 'NEURAL_NET', 'DEEP_LEARNING']
const modeColors = {
  'STANDBY': '#666666',
  'SCANNING': '#00ff88', 
  'PROCESSING': '#ffaa00',
  'ASSISTANT': '#0088ff',
  'PATROL': '#ff0088',
  'NEURAL_NET': '#8800ff',
  'DEEP_LEARNING': '#ff4400'
}

const aiMetrics = ref([
  { icon: '🧠', label: 'Neural Nodes', value: '2.1M' },
  { icon: '⚡', label: 'Synapses', value: '15.8B' },
  { icon: '🎯', label: 'Accuracy', value: '97.3%' },
  { icon: '🚀', label: 'Speed', value: '1.2ms' }
])

const performanceData = ref([
  { id: 1, height: 85 },
  { id: 2, height: 92 },
  { id: 3, height: 78 },
  { id: 4, height: 95 },
  { id: 5, height: 88 },
  { id: 6, height: 91 },
  { id: 7, height: 83 },
  { id: 8, height: 97 }
])

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

const toggleVoice = () => {
  voiceEnabled.value = !voiceEnabled.value
  if (!voiceEnabled.value) {
    // Stop any ongoing speech
    speechSynthesis.cancel()
  }
}

const cycleMode = () => {
  const currentIndex = modes.indexOf(robotMode.value)
  const nextIndex = (currentIndex + 1) % modes.length
  robotMode.value = modes[nextIndex]
  currentModeColor.value = modeColors[robotMode.value as keyof typeof modeColors] || '#00ff88'
  isProcessing.value = true
  setTimeout(() => {
    isProcessing.value = false
  }, 2000)
  speakText(`Switching to ${robotMode.value} mode`)
}

const resetSystem = () => {
  isProcessing.value = true
  setTimeout(() => {
    power.value = 100
    robotMode.value = 'STANDBY'
    currentModeColor.value = modeColors['STANDBY']
    isProcessing.value = false
    speakText('System reset complete')
  }, 3000)
}

const exportLogs = () => {
  speakText('Exporting system logs')
  console.log('Exporting NEXBOT logs...')
}

const openDiagnostics = () => {
  speakText('Opening system diagnostics')
  console.log('Opening NEXBOT diagnostics...')
}

const speakText = (text: string) => {
  if (!voiceEnabled.value || !('speechSynthesis' in window)) return
  
  speechSynthesis.cancel() // Stop any ongoing speech
  
  const utterance = new SpeechSynthesisUtterance(text)
  utterance.rate = 1.3
  utterance.pitch = 1.1
  utterance.volume = 0.7
  
  const voices = speechSynthesis.getVoices()
  const preferredVoice = voices.find(voice => 
    voice.name.includes('Google') || 
    voice.name.includes('Microsoft') ||
    voice.lang.startsWith('en')
  )
  if (preferredVoice) {
    utterance.voice = preferredVoice
  }
  
  speechSynthesis.speak(utterance)
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
  
  // Speak the complete message if voice is enabled
  if (voiceEnabled.value) {
    speakText(message)
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

// Auto-activate and start speaking
onMounted(() => {
  // Auto-activate robot
  setTimeout(() => {
    isActive.value = true
    animateRobotBehavior()
    startDialogueSystem()
    
    // Auto-speak welcome message
    speakText("Hello! I'm NEXBOT, Tri's AI assistant. I'm here to showcase his expertise in finance, technology, and entrepreneurship.")
  }, 1000)
  
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
/* NEXBOT Container & Layout */
.nexbot-container {
  background: linear-gradient(135deg, rgba(0, 0, 0, 0.95), rgba(10, 20, 40, 0.9));
  border: 1px solid rgba(100, 255, 200, 0.2);
  border-radius: 20px;
  padding: 2rem;
  margin: 2rem auto;
  max-width: 1400px;
  backdrop-filter: blur(15px);
  box-shadow: 
    0 0 50px rgba(0, 255, 136, 0.1),
    inset 0 0 50px rgba(0, 100, 255, 0.05);
  position: relative;
  overflow: hidden;
}

.nexbot-container::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: 
    radial-gradient(circle at 20% 80%, rgba(0, 255, 136, 0.05) 0%, transparent 50%),
    radial-gradient(circle at 80% 20%, rgba(0, 100, 255, 0.05) 0%, transparent 50%);
  pointer-events: none;
}

/* Header Section */
.nexbot-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.5rem 2rem;
  background: rgba(0, 0, 0, 0.8);
  border: 1px solid rgba(100, 255, 200, 0.3);
  border-radius: 15px;
  margin-bottom: 2rem;
  backdrop-filter: blur(10px);
}

.system-info {
  display: flex;
  align-items: center;
  gap: 2rem;
}

.system-badge {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.system-name {
  font-size: 1.5rem;
  font-weight: 700;
  background: linear-gradient(45deg, #00ff88, #00cc66);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  letter-spacing: 0.1em;
}

.system-version {
  font-size: 0.875rem;
  color: rgba(255, 255, 255, 0.6);
  font-weight: 400;
}

.status-indicators {
  display: flex;
  gap: 1.5rem;
  align-items: center;
}

.indicator {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.5rem 1rem;
  background: rgba(0, 0, 0, 0.5);
  border-radius: 20px;
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.indicator.active .indicator-dot {
  background: #00ff88;
  box-shadow: 0 0 15px #00ff88;
}

.indicator.processing .indicator-dot {
  background: #ffaa00;
  box-shadow: 0 0 15px #ffaa00;
  animation: processing-pulse 1s ease-in-out infinite;
}

.indicator-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: #666;
  transition: all 0.3s ease;
}

.network-indicator {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.signal-bars {
  display: flex;
  gap: 2px;
  align-items: flex-end;
}

.bar {
  width: 3px;
  background: #00ff88;
  border-radius: 1px;
  animation: signal-strength 2s ease-in-out infinite;
}

.bar:nth-child(1) { height: 6px; }
.bar:nth-child(2) { height: 10px; }
.bar:nth-child(3) { height: 14px; }
.bar:nth-child(4) { height: 18px; }

/* Control Panel */
.control-panel {
  display: flex;
  gap: 0.75rem;
}

.control-btn {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.25rem;
  padding: 0.75rem 1rem;
  background: rgba(0, 0, 0, 0.6);
  border: 1px solid rgba(100, 255, 200, 0.3);
  border-radius: 10px;
  color: rgba(255, 255, 255, 0.8);
  cursor: pointer;
  transition: all 0.3s ease;
  backdrop-filter: blur(5px);
  min-width: 70px;
}

.control-btn:hover {
  background: rgba(0, 255, 136, 0.1);
  border-color: #00ff88;
  color: #00ff88;
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(0, 255, 136, 0.2);
}

.control-btn.active {
  background: rgba(0, 255, 136, 0.2);
  border-color: #00ff88;
  color: #00ff88;
  box-shadow: 0 0 20px rgba(0, 255, 136, 0.3);
}

.control-btn svg {
  width: 20px;
  height: 20px;
  stroke-width: 2;
}

.control-btn span {
  font-size: 0.75rem;
  font-weight: 600;
  letter-spacing: 0.05em;
}

/* Main Display Area */
.nexbot-main {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
  align-items: flex-start;
}

/* Robot Display Area */
.robot-display-area {
  position: relative;
}

.hologram-frame {
  position: relative;
  aspect-ratio: 1;
  background: 
    radial-gradient(circle at center, rgba(0, 255, 136, 0.05) 0%, transparent 70%),
    linear-gradient(45deg, rgba(0, 100, 255, 0.02) 0%, rgba(0, 255, 136, 0.02) 100%);
  border: 2px solid rgba(0, 255, 136, 0.3);
  border-radius: 20px;
  overflow: hidden;
  backdrop-filter: blur(10px);
}

.scan-lines {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: repeating-linear-gradient(
    0deg,
    transparent 0px,
    rgba(0, 255, 136, 0.03) 1px,
    transparent 2px
  );
  animation: scan-sweep 3s linear infinite;
  pointer-events: none;
}

.grid-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  opacity: 0.2;
}

.grid-line {
  position: absolute;
  background: rgba(0, 255, 136, 0.1);
}

.grid-line:not(.vertical) {
  width: 100%;
  height: 1px;
  top: calc(12.5% * var(--index, 1));
}

.grid-line.vertical {
  height: 100%;
  width: 1px;
  left: calc(12.5% * var(--index, 1));
}

/* Enhanced 3D Robot */
.nexbot-3d {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  transform-style: preserve-3d;
  transition: all 0.5s ease;
}

.nexbot-3d.active {
  animation: robot-float 4s ease-in-out infinite;
}

.nexbot-3d.processing {
  animation: robot-processing 2s ease-in-out infinite;
}

/* Robot Head */
.robot-head {
  position: relative;
  width: 120px;
  height: 120px;
  margin: 0 auto 20px;
}

.head-shell {
  width: 100%;
  height: 100%;
  background: 
    linear-gradient(135deg, rgba(50, 50, 70, 0.9), rgba(20, 20, 40, 0.9)),
    radial-gradient(circle at 30% 30%, rgba(255, 255, 255, 0.1), transparent);
  border: 2px solid rgba(100, 200, 255, 0.4);
  border-radius: 50% 50% 45% 45%;
  position: relative;
  overflow: hidden;
  box-shadow: 
    0 0 30px rgba(0, 100, 255, 0.3),
    inset 0 0 20px rgba(255, 255, 255, 0.05);
}

.head-surface {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(45deg, transparent 40%, rgba(255, 255, 255, 0.1) 50%, transparent 60%);
  animation: surface-shine 3s ease-in-out infinite;
}

.head-reflections {
  position: absolute;
  top: 20%;
  left: 20%;
  width: 25px;
  height: 35px;
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.3), transparent);
  border-radius: 50%;
  filter: blur(2px);
}

/* Advanced Eyes */
.eye-system {
  position: absolute;
  top: 35%;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 35px;
  align-items: center;
}

.eye {
  position: relative;
  width: 25px;
  height: 25px;
}

.eye-lens {
  width: 100%;
  height: 100%;
  background: 
    radial-gradient(circle at 30% 30%, rgba(255, 255, 255, 0.8), rgba(200, 200, 255, 0.9)),
    linear-gradient(45deg, rgba(0, 100, 255, 0.3), rgba(0, 255, 136, 0.3));
  border-radius: 50%;
  position: relative;
  overflow: hidden;
  box-shadow: 0 0 15px rgba(0, 200, 255, 0.5);
}

.iris {
  position: absolute;
  top: 20%;
  left: 20%;
  width: 60%;
  height: 60%;
  border-radius: 50%;
  background: #00ff88;
  transition: background-color 0.3s ease;
}

.pupil {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 40%;
  height: 40%;
  background: #000;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.scan-beam {
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, transparent, rgba(255, 0, 0, 0.8), transparent);
  animation: scan-beam 1s ease-in-out infinite;
}

.eye-glow {
  position: absolute;
  top: -5px;
  left: -5px;
  right: -5px;
  bottom: -5px;
  border-radius: 50%;
  pointer-events: none;
  transition: box-shadow 0.3s ease;
}

/* Neural Network */
.neural-network {
  position: absolute;
  top: 70%;
  left: 50%;
  transform: translateX(-50%);
  width: 80px;
  height: 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.neural-node {
  width: 4px;
  height: 4px;
  background: #00ff88;
  border-radius: 50%;
  animation: neural-pulse 2s ease-in-out infinite;
  box-shadow: 0 0 8px #00ff88;
}

.neural-connection {
  position: absolute;
  width: 100%;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(0, 255, 136, 0.3), transparent);
  top: 50%;
  animation: data-flow 1.5s linear infinite;
}

/* Antenna Array */
.antenna-array {
  position: absolute;
  top: -10px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 8px;
  align-items: flex-end;
}

.antenna.primary {
  width: 3px;
  height: 25px;
  background: linear-gradient(to top, rgba(100, 200, 255, 0.8), rgba(0, 255, 136, 1));
  border-radius: 1.5px;
  position: relative;
}

.antenna.primary.transmitting {
  animation: antenna-transmit 1s ease-in-out infinite;
}

.antenna-tip {
  position: absolute;
  top: -3px;
  left: 50%;
  transform: translateX(-50%);
  width: 6px;
  height: 6px;
  background: #00ff88;
  border-radius: 50%;
  box-shadow: 0 0 10px #00ff88;
}

.signal-ring {
  position: absolute;
  top: -5px;
  left: 50%;
  transform: translateX(-50%);
  width: 15px;
  height: 15px;
  border: 1px solid rgba(0, 255, 136, 0.6);
  border-radius: 50%;
  animation: signal-expand 2s ease-out infinite;
}

.signal-ring:nth-child(2) { animation-delay: 0.3s; }
.signal-ring:nth-child(3) { animation-delay: 0.6s; }

.antenna.secondary {
  width: 2px;
  height: 15px;
  background: rgba(100, 200, 255, 0.6);
  border-radius: 1px;
}

/* Robot Body */
.robot-body {
  position: relative;
  width: 100px;
  height: 80px;
  margin: 0 auto;
}

.body-core {
  width: 100%;
  height: 100%;
  background: 
    linear-gradient(135deg, rgba(40, 40, 60, 0.9), rgba(20, 20, 30, 0.9)),
    radial-gradient(circle at center, rgba(0, 255, 136, 0.1), transparent);
  border: 2px solid rgba(100, 200, 255, 0.4);
  border-radius: 15px;
  position: relative;
  overflow: hidden;
}

.power-core {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: #00ff88;
  box-shadow: 0 0 20px currentColor;
  animation: power-pulse 2s ease-in-out infinite;
}

.energy-flow {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}

.flow-particle {
  position: absolute;
  width: 3px;
  height: 3px;
  background: #00ff88;
  border-radius: 50%;
  animation: energy-flow 3s linear infinite;
  box-shadow: 0 0 6px currentColor;
}

.flow-particle:nth-child(1) { top: 20%; left: 20%; animation-delay: 0s; }
.flow-particle:nth-child(2) { top: 20%; right: 20%; animation-delay: 0.5s; }
.flow-particle:nth-child(3) { bottom: 20%; left: 20%; animation-delay: 1s; }
.flow-particle:nth-child(4) { bottom: 20%; right: 20%; animation-delay: 1.5s; }
.flow-particle:nth-child(5) { top: 50%; left: 10%; animation-delay: 2s; }
.flow-particle:nth-child(6) { top: 50%; right: 10%; animation-delay: 2.5s; }

.chest-panel {
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  gap: 5px;
  align-items: center;
}

.panel-display {
  display: flex;
  flex-direction: column;
  gap: 2px;
}

.display-line {
  width: 30px;
  height: 1px;
  background: rgba(0, 255, 136, 0.6);
  animation: display-flicker 2s ease-in-out infinite;
}

.status-lights {
  display: flex;
  gap: 3px;
}

.status-light {
  width: 4px;
  height: 4px;
  background: rgba(100, 100, 100, 0.3);
  border-radius: 50%;
  transition: all 0.3s ease;
}

.status-light.active {
  background: #00ff88;
  box-shadow: 0 0 6px #00ff88;
}

/* Holographic Elements */
.holo-elements {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  pointer-events: none;
}

.data-stream {
  position: absolute;
  display: flex;
  flex-direction: column;
  gap: 5px;
  animation: stream-float 4s ease-in-out infinite;
}

.data-stream:nth-child(1) { top: 10%; left: 10%; animation-delay: 0s; }
.data-stream:nth-child(2) { top: 15%; right: 15%; animation-delay: 1s; }
.data-stream:nth-child(3) { bottom: 20%; left: 20%; animation-delay: 2s; }
.data-stream:nth-child(4) { bottom: 25%; right: 10%; animation-delay: 3s; }

.data-bit {
  width: 2px;
  height: 2px;
  background: rgba(0, 255, 136, 0.7);
  border-radius: 50%;
  animation: bit-twinkle 1s ease-in-out infinite;
}

/* Information Panels */
.info-panels {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.panel {
  background: rgba(0, 0, 0, 0.8);
  border: 1px solid rgba(100, 200, 255, 0.3);
  border-radius: 15px;
  padding: 1.5rem;
  backdrop-filter: blur(10px);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
  transition: all 0.3s ease;
}

.panel:hover {
  border-color: rgba(0, 255, 136, 0.5);
  box-shadow: 0 6px 25px rgba(0, 255, 136, 0.1);
}

.panel-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  padding-bottom: 0.5rem;
}

.panel-header h4 {
  color: #ffffff;
  font-size: 0.875rem;
  font-weight: 600;
  letter-spacing: 0.1em;
  margin: 0;
}

.panel-indicator {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: #00ff88;
  box-shadow: 0 0 10px currentColor;
}

.panel-indicator.optimal {
  background: #00ff88;
  animation: optimal-pulse 2s ease-in-out infinite;
}

.panel-indicator.pulsing {
  animation: analytics-pulse 1.5s ease-in-out infinite;
}

/* Status Panel */
.status-grid {
  display: grid;
  gap: 0.75rem;
  margin-bottom: 1rem;
}

.status-item {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  font-size: 0.75rem;
}

.status-item .label {
  color: rgba(255, 255, 255, 0.7);
  font-weight: 600;
  min-width: 35px;
}

.progress-bar {
  flex: 1;
  height: 6px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 3px;
  overflow: hidden;
  position: relative;
}

.progress-fill {
  height: 100%;
  background: linear-gradient(90deg, #00ff88, #00cc66);
  border-radius: 3px;
  transition: width 0.3s ease;
  box-shadow: 0 0 8px rgba(0, 255, 136, 0.5);
  position: relative;
}

.progress-fill::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
  animation: progress-shine 2s ease-in-out infinite;
}

.status-item .value {
  color: #00ff88;
  font-weight: 700;
  min-width: 35px;
  text-align: right;
}

.system-mode {
  display: flex;
  gap: 0.5rem;
  align-items: center;
  font-size: 0.75rem;
}

.mode-label {
  color: rgba(255, 255, 255, 0.7);
  font-weight: 600;
}

.mode-value {
  font-weight: 700;
  letter-spacing: 0.05em;
}

/* Analytics Panel */
.analytics-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}

.metric-card {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.75rem;
  background: rgba(0, 0, 0, 0.4);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 10px;
  transition: all 0.3s ease;
}

.metric-card:hover {
  background: rgba(0, 255, 136, 0.05);
  border-color: rgba(0, 255, 136, 0.3);
  transform: translateY(-2px);
}

.metric-icon {
  font-size: 1.25rem;
  filter: grayscale(0.3);
}

.metric-info {
  flex: 1;
}

.metric-value {
  color: #00ff88;
  font-size: 1rem;
  font-weight: 700;
  line-height: 1;
}

.metric-label {
  color: rgba(255, 255, 255, 0.6);
  font-size: 0.625rem;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}

/* Communication Panel */
.message-display {
  display: flex;
  gap: 1rem;
  align-items: flex-start;
  margin-bottom: 1rem;
}

.message-avatar {
  position: relative;
  width: 35px;
  height: 35px;
  background: rgba(0, 0, 0, 0.6);
  border: 2px solid #00ff88;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.75rem;
  font-weight: 700;
  color: #00ff88;
  flex-shrink: 0;
}

.avatar-glow {
  position: absolute;
  top: -3px;
  left: -3px;
  right: -3px;
  bottom: -3px;
  border-radius: 50%;
  opacity: 0.3;
  animation: avatar-glow 2s ease-in-out infinite;
}

.message-content {
  flex: 1;
  background: rgba(0, 0, 0, 0.4);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 10px;
  padding: 0.75rem;
  min-height: 40px;
  display: flex;
  align-items: center;
}

.typing-animation {
  display: flex;
  gap: 4px;
  align-items: center;
}

.typing-dot {
  width: 6px;
  height: 6px;
  background: #00ff88;
  border-radius: 50%;
  animation: typing-pulse 1.5s ease-in-out infinite;
}

.typing-dot:nth-child(2) { animation-delay: 0.3s; }
.typing-dot:nth-child(3) { animation-delay: 0.6s; }

.message-text {
  color: rgba(255, 255, 255, 0.9);
  font-size: 0.8rem;
  line-height: 1.4;
  margin: 0;
}

.response-stats {
  display: flex;
  justify-content: space-between;
  font-size: 0.7rem;
}

.stat {
  display: flex;
  gap: 0.25rem;
}

.stat-label {
  color: rgba(255, 255, 255, 0.6);
}

.stat-value {
  color: #00ff88;
  font-weight: 600;
}

/* Performance Panel */
.performance-chart {
  margin-bottom: 1rem;
}

.chart-bars {
  display: flex;
  align-items: flex-end;
  gap: 4px;
  height: 60px;
  margin-bottom: 0.5rem;
}

.chart-bar {
  flex: 1;
  background: #00ff88;
  border-radius: 2px 2px 0 0;
  min-height: 5px;
  transition: all 0.3s ease;
  position: relative;
  opacity: 0.8;
}

.chart-bar:hover {
  opacity: 1;
  box-shadow: 0 0 10px currentColor;
}

.chart-labels {
  display: flex;
  justify-content: space-between;
  font-size: 0.65rem;
  color: rgba(255, 255, 255, 0.5);
}

.performance-stats {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 1rem;
}

.perf-stat {
  text-align: center;
}

.perf-value {
  display: block;
  color: #00ff88;
  font-size: 1.1rem;
  font-weight: 700;
  line-height: 1;
}

.perf-label {
  color: rgba(255, 255, 255, 0.6);
  font-size: 0.65rem;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}

/* Footer */
.nexbot-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.5rem 2rem;
  background: rgba(0, 0, 0, 0.8);
  border: 1px solid rgba(100, 255, 200, 0.2);
  border-radius: 15px;
  margin-top: 2rem;
  backdrop-filter: blur(10px);
}

.footer-stats {
  display: flex;
  gap: 2rem;
}

.stat-item {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.8rem;
}

.stat-icon {
  font-size: 1rem;
  filter: grayscale(0.3);
}

.stat-text {
  color: rgba(255, 255, 255, 0.7);
}

.footer-controls {
  display: flex;
  gap: 1rem;
}

.footer-btn {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.5rem 1rem;
  background: rgba(0, 0, 0, 0.6);
  border: 1px solid rgba(100, 255, 200, 0.3);
  border-radius: 8px;
  color: rgba(255, 255, 255, 0.8);
  font-size: 0.75rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.footer-btn:hover {
  background: rgba(0, 255, 136, 0.1);
  border-color: #00ff88;
  color: #00ff88;
  transform: translateY(-1px);
}

.footer-btn svg {
  width: 16px;
  height: 16px;
  stroke-width: 2;
}

/* Animations */
@keyframes robot-float {
  0%, 100% { transform: translate(-50%, -50%) translateY(0) rotateY(0deg); }
  25% { transform: translate(-50%, -50%) translateY(-5px) rotateY(5deg); }
  50% { transform: translate(-50%, -50%) translateY(0) rotateY(0deg); }
  75% { transform: translate(-50%, -50%) translateY(-3px) rotateY(-5deg); }
}

@keyframes robot-processing {
  0%, 100% { transform: translate(-50%, -50%) scale(1); }
  50% { transform: translate(-50%, -50%) scale(1.05); }
}

@keyframes scan-sweep {
  0% { transform: translateY(100%); }
  100% { transform: translateY(-100%); }
}

@keyframes surface-shine {
  0%, 100% { transform: translateX(-100%); }
  50% { transform: translateX(100%); }
}

@keyframes scan-beam {
  0%, 100% { transform: translateY(-50%) scaleX(0); }
  50% { transform: translateY(-50%) scaleX(1); }
}

@keyframes neural-pulse {
  0%, 100% { opacity: 0.5; transform: scale(1); }
  50% { opacity: 1; transform: scale(1.2); }
}

@keyframes data-flow {
  0% { transform: translateX(-100%) scaleX(0); }
  50% { transform: translateX(0) scaleX(1); }
  100% { transform: translateX(100%) scaleX(0); }
}

@keyframes antenna-transmit {
  0%, 100% { box-shadow: 0 0 5px currentColor; }
  50% { box-shadow: 0 0 20px currentColor, 0 0 30px currentColor; }
}

@keyframes signal-expand {
  0% {
    opacity: 1;
    transform: translateX(-50%) scale(0.5);
  }
  100% {
    opacity: 0;
    transform: translateX(-50%) scale(2);
  }
}

@keyframes power-pulse {
  0%, 100% { transform: translate(-50%, -50%) scale(1); box-shadow: 0 0 20px currentColor; }
  50% { transform: translate(-50%, -50%) scale(1.1); box-shadow: 0 0 30px currentColor; }
}

@keyframes energy-flow {
  0%, 100% { opacity: 0.3; transform: scale(0.8); }
  50% { opacity: 1; transform: scale(1.2); }
}

@keyframes display-flicker {
  0%, 100% { opacity: 0.6; }
  50% { opacity: 1; }
}

@keyframes stream-float {
  0%, 100% { transform: translateY(0) rotate(0deg); }
  50% { transform: translateY(-10px) rotate(5deg); }
}

@keyframes bit-twinkle {
  0%, 100% { opacity: 0.3; }
  50% { opacity: 1; }
}

@keyframes processing-pulse {
  0%, 100% { opacity: 0.7; }
  50% { opacity: 1; }
}

@keyframes signal-strength {
  0%, 100% { opacity: 0.6; }
  50% { opacity: 1; }
}

@keyframes optimal-pulse {
  0%, 100% { opacity: 0.8; }
  50% { opacity: 1; }
}

@keyframes analytics-pulse {
  0%, 100% { opacity: 0.6; transform: scale(1); }
  50% { opacity: 1; transform: scale(1.1); }
}

@keyframes progress-shine {
  0% { transform: translateX(-100%); }
  100% { transform: translateX(100%); }
}

@keyframes avatar-glow {
  0%, 100% { opacity: 0.3; }
  50% { opacity: 0.6; }
}

@keyframes typing-pulse {
  0%, 60%, 100% {
    transform: scale(1);
    opacity: 0.5;
  }
  30% {
    transform: scale(1.3);
    opacity: 1;
  }
}

/* Responsive Design */
@media (max-width: 1200px) {
  .nexbot-main {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .robot-display-area {
    max-width: 400px;
    margin: 0 auto;
  }
}

@media (max-width: 768px) {
  .nexbot-container {
    padding: 1rem;
    margin: 1rem;
  }
  
  .nexbot-header {
    flex-direction: column;
    gap: 1rem;
    padding: 1rem;
  }
  
  .system-info {
    flex-direction: column;
    gap: 1rem;
    text-align: center;
  }
  
  .analytics-grid {
    grid-template-columns: 1fr;
  }
  
  .performance-stats {
    grid-template-columns: 1fr;
  }
  
  .footer-stats {
    flex-direction: column;
    gap: 0.5rem;
  }
  
  .footer-controls {
    flex-direction: column;
    gap: 0.5rem;
  }
}
</style> 