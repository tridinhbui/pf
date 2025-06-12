<template>
  <div class="chatbot-container">
    <!-- Robot Face Chat Button -->
    <button 
      class="chat-button robot-face-btn"
      @click="toggleChat"
      :class="{ 'active': isOpen }"
    >
      <div class="robot-face">
        <div class="robot-head">
          <div class="robot-antenna left"></div>
          <div class="robot-antenna right"></div>
          <div class="robot-face-shell">
            <div class="robot-eyes">
              <div class="robot-eye left">
                <div class="eye-pupil"></div>
                <div class="eye-glow"></div>
              </div>
              <div class="robot-eye right">
                <div class="eye-pupil"></div>
                <div class="eye-glow"></div>
              </div>
            </div>
            <div class="robot-mouth">
              <div class="mouth-line" v-for="n in 3" :key="n"></div>
            </div>
            <div class="robot-cheek-vents">
              <div class="vent left"></div>
              <div class="vent right"></div>
            </div>
          </div>
        </div>
      </div>
      <div class="pulse-ring"></div>
      <div class="floating-particles">
        <div class="particle" v-for="n in 8" :key="n"></div>
      </div>
    </button>

    <!-- Chat Interface -->
    <transition name="chat-slide">
      <div v-if="isOpen" class="chat-interface">
        <!-- Header -->
        <div class="chat-header">
          <div class="bot-avatar">
            <div class="avatar-icon">🤖</div>
            <div class="status-indicator"></div>
          </div>
          <div class="bot-info">
            <h3>Tri AI Assistant</h3>
            <p>Online • Usually replies instantly</p>
          </div>
          <div class="chat-controls">
            <button 
              @click="toggleChatMute" 
              class="chat-mute-btn" 
              :class="{ 'muted': isChatMuted }"
              :title="isChatMuted ? 'Unmute Chat Audio' : 'Mute Chat Audio'"
            >
              <span v-if="!isChatMuted">🔊</span>
              <span v-else>🔇</span>
            </button>
          </div>
        </div>

        <!-- Messages -->
        <div class="chat-messages" ref="messagesContainer">
          <div 
            v-for="message in messages" 
            :key="message.id"
            class="message"
            :class="{ 'user': message.sender === 'user', 'bot': message.sender === 'bot' }"
          >
            <div class="message-avatar" v-if="message.sender === 'bot'">🤖</div>
            <div class="message-content">
              <div class="message-bubble" v-html="message.text.replace(/\\n/g, '<br>')">
              </div>
              <div class="message-time">{{ message.time }}</div>
            </div>
            <div class="message-avatar" v-if="message.sender === 'user'">👤</div>
          </div>
          
          <!-- Typing Indicator -->
          <div v-if="isTyping" class="message bot">
            <div class="message-avatar">🤖</div>
            <div class="message-content">
              <div class="typing-indicator">
                <div class="typing-dot"></div>
                <div class="typing-dot"></div>
                <div class="typing-dot"></div>
              </div>
            </div>
          </div>
        </div>

        <!-- Quick Actions Carousel -->
        <div class="quick-actions-container">
          <div class="quick-actions-carousel" ref="carouselRef">
            <div class="quick-actions-row">
              <button 
                v-for="action in quickActionsRow1" 
                :key="action.id"
                class="quick-action-btn"
                @click="sendQuickMessage(action.text)"
              >
                {{ action.text }}
              </button>
            </div>
            <div class="quick-actions-row">
              <button 
                v-for="action in quickActionsRow2" 
                :key="action.id"
                class="quick-action-btn"
                @click="sendQuickMessage(action.text)"
              >
                {{ action.text }}
              </button>
            </div>
          </div>
          <div class="carousel-dots">
            <div class="dot" :class="{ active: currentRow === 0 }" @click="switchRow(0)"></div>
            <div class="dot" :class="{ active: currentRow === 1 }" @click="switchRow(1)"></div>
          </div>
        </div>

        <!-- Input -->
        <div class="chat-input">
          <div class="input-container">
            <input 
              v-model="currentMessage"
              @keydown.enter="sendMessage"
              placeholder="Type your message..."
              class="message-input"
              :disabled="isTyping"
            />
            <button 
              @click="sendMessage"
              class="send-button"
              :disabled="!currentMessage.trim() || isTyping"
            >
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8"/>
              </svg>
            </button>
          </div>
        </div>
      </div>
    </transition>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, nextTick, watch } from 'vue'

const props = defineProps({
  autoOpen: {
    type: Boolean,
    default: false
  }
})

interface Message {
  id: number;
  text: string;
  sender: 'user' | 'bot';
  time: string;
}

interface QuickAction {
  id: number;
  text: string;
}

const isOpen = ref(false)
const currentMessage = ref('')
const isTyping = ref(false)
const messagesContainer = ref<HTMLElement>()
const carouselRef = ref<HTMLElement>()
const currentRow = ref(0)
const isChatMuted = ref(false)
const isCurrentlySpeaking = ref(false)

const messages = ref<Message[]>([
  {
    id: 1,
    text: "Hello! I'm Tri's AI Assistant. I can help you learn about his experience in finance, technology, and entrepreneurship. How can I assist you today?",
    sender: 'bot',
    time: new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' })
  }
])

const quickActionsRow1 = ref<QuickAction[]>([
  { id: 1, text: "Tell me about Tri's finance experience" },
  { id: 2, text: "What are his top AI/ML projects?" },
  { id: 3, text: "How can I contact Tri?" },
  { id: 4, text: "What's his entrepreneurship philosophy?" }
])

const quickActionsRow2 = ref<QuickAction[]>([
  { id: 5, text: "What are his technical skills?" },
  { id: 6, text: "Tell me about his education" },
  { id: 7, text: "What makes him unique?" },
  { id: 8, text: "Schedule a meeting with Tri" }
])

const botResponses: { [key: string]: string | string[] } = {
  default: "Thank you for your question. I'll ask Tri and get back to you as soon as possible. In the meantime, do you have any other questions about his experience, projects, or skills?",
  greeting: "Hello! How can I help you today?",
  experience: [
    "Tri has extensive experience in corporate finance and investment analysis. At Smithfield Foods, he's responsible for modeling CAPEX projects and optimizing debt structure for over $1 billion in assets.",
    "At Blackstone, Tri built a Monte Carlo model in Python for rent stress-testing, helping identify and mitigate $1.5 million in potential downside risk.",
    "His experience also includes risk analysis at Deloitte and due diligence for Climate Tech startups at Caprae Private Equity."
  ],
  projects: "Tri has founded and developed several technology projects, most notably:\\n- **FinBud AI:** A personal finance AI assistant using NLP models to understand user requests and time-series forecasting algorithms to provide financial advice.\\n- **NextGen Investor:** Co-founded a financial education platform empowering aspiring investors with practical knowledge and mentorship networks.",
  skills: "Tri has a diverse skill set:\\n- **Languages:** Python, JavaScript/TypeScript, SQL, R\\n- **Frameworks:** Vue.js, React, Node.js, TensorFlow, PyTorch\\n- **Infrastructure:** AWS (Lambda, S3, EC2), Docker, CI/CD\\n- **AI/ML:** Natural Language Processing (NLP), Time-Series Forecasting, LLM Fine-tuning, Computer Vision (Object Detection)\\n- **Databases:** Experience with PostgreSQL, MongoDB, and vector databases",
  philosophy: "Tri's philosophy is building sustainable ecosystems rather than individual products. He believes in 'learn fast, teach faster,' 'build systems, not barriers,' and always 'lift others as you climb.'",
  contact: "You can reach Tri via email at tbui@macalester.edu or connect via LinkedIn: linkedin.com/in/tribuidinh",
  schedule: "To schedule a meeting, you can email Tri directly with your preferred time. He'll respond as soon as possible.",
  education: "Tri graduated from Macalester College with a dual degree in Computer Science and Quantitative Economics. He was a $230K Kofi Annan Scholar and made Dean's List for all 6 semesters. He also completed an exchange program at NTU Singapore.",
  unique: "What makes Tri unique is his ability to bridge three worlds: technology, finance, and entrepreneurship. He's not just building products, but entire ecosystems that create lasting impact for ambitious professionals."
}

const getBotResponse = (userMessage: string): string => {
  const lowerCaseMessage = userMessage.toLowerCase();
  if (lowerCaseMessage.includes('experience') || lowerCaseMessage.includes('finance') || lowerCaseMessage.includes('work')) {
    const responses = botResponses.experience as string[];
    return responses.join('\\n\\n');
  }
  if (lowerCaseMessage.includes('project') || lowerCaseMessage.includes('ai') || lowerCaseMessage.includes('ml') || lowerCaseMessage.includes('technology')) {
    return botResponses.projects as string;
  }
  if (lowerCaseMessage.includes('skill') || lowerCaseMessage.includes('technical') || lowerCaseMessage.includes('programming')) {
    return botResponses.skills as string;
  }
  if (lowerCaseMessage.includes('philosophy') || lowerCaseMessage.includes('entrepreneurship') || lowerCaseMessage.includes('unique') || lowerCaseMessage.includes('different')) {
    return botResponses.philosophy as string;
  }
  if (lowerCaseMessage.includes('contact') || lowerCaseMessage.includes('email') || lowerCaseMessage.includes('reach')) {
    return botResponses.contact as string;
  }
  if (lowerCaseMessage.includes('meeting') || lowerCaseMessage.includes('schedule') || lowerCaseMessage.includes('appointment')) {
    return botResponses.schedule as string;
  }
  if (lowerCaseMessage.includes('education') || lowerCaseMessage.includes('college') || lowerCaseMessage.includes('school')) {
    return botResponses.education as string;
  }
  if (lowerCaseMessage.includes('hello') || lowerCaseMessage.includes('hi') || lowerCaseMessage.includes('hey')) {
    return botResponses.greeting as string;
  }
  return botResponses.default as string;
}

const switchRow = (rowIndex: number) => {
  currentRow.value = rowIndex;
  if (carouselRef.value) {
    carouselRef.value.style.transform = `translateY(-${rowIndex * 50}%)`;
  }
}

const speakText = (text: string) => {
  if (!('speechSynthesis' in window) || isChatMuted.value || isCurrentlySpeaking.value) return
  
  // Remove HTML tags and decode HTML entities
  const plainText = text.replace(/<[^>]*>/g, '').replace(/&[^;]+;/g, ' ').replace(/\\n/g, ' ')
  
  isCurrentlySpeaking.value = true
  const utterance = new SpeechSynthesisUtterance(plainText)
  
  // Configure voice settings - slower and clearer
  utterance.rate = 0.7 // Slower for better understanding
  utterance.pitch = 1.0
  utterance.volume = 0.7
    
    // Try to use a more natural voice
    const voices = speechSynthesis.getVoices();
    const preferredVoice = voices.find(voice => 
      voice.name.includes('Google') || 
      voice.name.includes('Microsoft') ||
      voice.lang.startsWith('en')
    );
    if (preferredVoice) {
      utterance.voice = preferredVoice;
    }
    
  utterance.onend = () => {
    isCurrentlySpeaking.value = false
  }
  
  utterance.onerror = () => {
    isCurrentlySpeaking.value = false
  }
  
    speechSynthesis.speak(utterance);
}

const toggleChat = () => {
  isOpen.value = !isOpen.value
}

watch(() => props.autoOpen, (newValue) => {
  if (newValue) {
    setTimeout(() => {
      isOpen.value = true;
      // Auto-speak welcome message if not muted
      if (!isChatMuted.value) {
      setTimeout(() => {
        speakText(messages.value[0].text);
      }, 500);
      }
    }, 3000)
  }
});

// Auto-rotate carousel every 5 seconds
setInterval(() => {
  currentRow.value = (currentRow.value + 1) % 2;
  switchRow(currentRow.value);
}, 5000);

const sendMessage = async () => {
  if (!currentMessage.value.trim() || isTyping.value) return

  // Add user message
  const userMessage: Message = {
    id: Date.now(),
    text: currentMessage.value,
    sender: 'user',
    time: new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' })
  }
  messages.value.push(userMessage)
  
  const messageText = currentMessage.value
  currentMessage.value = ''
  
  // Show typing indicator
  isTyping.value = true
  await nextTick()
  scrollToBottom()

  // Simulate bot response delay
  setTimeout(() => {
    const botResponse = getBotResponse(messageText)
    const botMessage: Message = {
      id: Date.now() + 1,
      text: botResponse,
      sender: 'bot',
      time: new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' })
    }
    
    messages.value.push(botMessage)
    isTyping.value = false
    
    nextTick(() => {
      scrollToBottom()
      // Auto-speak bot response if not muted
      if (!isChatMuted.value) {
      speakText(botResponse)
      }
    })
  }, 1000 + Math.random() * 1000)
}

const sendQuickMessage = (message: string) => {
  currentMessage.value = message
  sendMessage()
}

const scrollToBottom = () => {
  if (messagesContainer.value) {
    messagesContainer.value.scrollTop = messagesContainer.value.scrollHeight
  }
}

const toggleChatMute = () => {
  isChatMuted.value = !isChatMuted.value
  if (isChatMuted.value && isCurrentlySpeaking.value) {
    speechSynthesis.cancel()
    isCurrentlySpeaking.value = false
  }
}

onMounted(() => {
  scrollToBottom()
})
</script>

<style scoped>
.chatbot-container {
  position: fixed;
  bottom: 20px;
  right: 20px;
  z-index: 1000;
}

/* Chat Button */
.chat-button {
  position: relative;
  width: 60px;
  height: 60px;
  background: linear-gradient(135deg, #000000, #333333);
  border: none;
  border-radius: 50%;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
  transition: all 0.3s ease;
  overflow: hidden;
}

.chat-button:hover {
  transform: scale(1.1);
  box-shadow: 0 6px 25px rgba(0, 0, 0, 0.4);
}

.chat-button.active {
  background: linear-gradient(135deg, #333333, #555555);
}

.button-icon {
  width: 28px;
  height: 28px;
  color: #ffffff;
  transition: transform 0.3s ease;
}

.pulse-ring {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  border: 2px solid #000000;
  border-radius: 50%;
  animation: pulse-animation 2s infinite;
  opacity: 0;
}

@keyframes pulse-animation {
  0% {
    transform: scale(0.95);
    opacity: 0.7;
  }
  70% {
    transform: scale(1.4);
    opacity: 0;
  }
  100% {
    transform: scale(0.95);
    opacity: 0;
  }
}

/* Chat Interface */
.chat-interface {
  position: absolute;
  bottom: 80px;
  right: 0;
  width: 370px;
  max-width: 90vw;
  height: 600px;
  max-height: 80vh;
  background-color: #ffffff;
  border-radius: 16px;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.2);
  display: flex;
  flex-direction: column;
  overflow: hidden;
  border: 1px solid #e5e5e5;
}

.chat-slide-enter-active, .chat-slide-leave-active {
  transition: transform 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275), opacity 0.4s ease;
}

.chat-slide-enter-from, .chat-slide-leave-to {
  transform: translateY(20px) scale(0.95);
  opacity: 0;
}

/* Chat Header */
.chat-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px 20px;
  background-color: #f9f9f9;
  border-bottom: 1px solid #e5e5e5;
  flex-shrink: 0;
}

.chat-controls {
  display: flex;
  gap: 0.5rem;
}

.chat-mute-btn {
  background: rgba(0, 0, 0, 0.1);
  border: 1px solid rgba(0, 0, 0, 0.2);
  color: #333333;
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

.chat-mute-btn:hover {
  background: rgba(0, 0, 0, 0.2);
  border-color: rgba(0, 0, 0, 0.4);
}

.chat-mute-btn.muted {
  background: rgba(255, 68, 68, 0.2);
  border-color: #ff4444;
  color: #ff4444;
}

.bot-avatar {
  position: relative;
  margin-right: 12px;
}

.avatar-icon {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  background: #e9ecef;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
}

.status-indicator {
  position: absolute;
  bottom: 1px;
  right: 1px;
  width: 12px;
  height: 12px;
  background-color: #28a745;
  border: 2px solid #ffffff;
  border-radius: 50%;
}

.bot-info h3 {
  margin: 0;
  font-size: 16px;
  font-weight: 600;
  color: #333333;
}

.bot-info p {
  margin: 0;
  font-size: 13px;
  color: #666666;
}

/* Messages */
.chat-messages {
  flex-grow: 1;
  padding: 20px;
  overflow-y: auto;
}

.message {
  display: flex;
  margin-bottom: 16px;
  max-width: 85%;
}

.message.user {
  margin-left: auto;
  flex-direction: row-reverse;
}

.message-avatar {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background: #e9ecef;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 18px;
  flex-shrink: 0;
  margin: 0 10px;
}

.message-content {
  display: flex;
  flex-direction: column;
}

.message.user .message-content {
  align-items: flex-end;
}

.message-bubble {
  padding: 12px 16px;
  border-radius: 18px;
  font-size: 15px;
  line-height: 1.5;
  word-wrap: break-word;
}

.message.bot .message-bubble {
  background-color: #f1f3f5;
  color: #333333;
  border-bottom-left-radius: 4px;
}

.message.user .message-bubble {
  background-color: #000000;
  color: #ffffff;
  border-bottom-right-radius: 4px;
}

.message-time {
  margin-top: 4px;
  font-size: 11px;
  color: #999999;
  padding: 0 8px;
}

/* Typing Indicator */
.typing-indicator {
  display: flex;
  align-items: center;
  padding: 12px 16px;
}

.typing-dot {
  width: 8px;
  height: 8px;
  background-color: #ced4da;
  border-radius: 50%;
  margin: 0 2px;
  animation: typing-animation 1.2s infinite ease-in-out;
}

.typing-dot:nth-child(2) { animation-delay: 0.2s; }
.typing-dot:nth-child(3) { animation-delay: 0.4s; }

@keyframes typing-animation {
  0%, 80%, 100% {
    transform: scale(0);
  }
  40% {
    transform: scale(1);
  }
}

/* Quick Actions Container */
.quick-actions-container {
  padding: 10px 20px;
  border-top: 1px solid #e5e5e5;
  display: flex;
  flex-direction: column;
  flex-shrink: 0;
}

/* Quick Actions Carousel */
.quick-actions-carousel {
  height: 80px;
  overflow: hidden;
  position: relative;
  transition: transform 0.3s ease;
}

.quick-actions-row {
  display: flex;
  gap: 8px;
  height: 40px;
  align-items: center;
}

.quick-action-btn {
  padding: 8px 12px;
  background-color: #ffffff;
  border: 1px solid #ced4da;
  border-radius: 16px;
  cursor: pointer;
  font-size: 13px;
  color: #495057;
  transition: all 0.2s ease;
}

.quick-action-btn:hover {
  background-color: #f1f3f5;
  border-color: #adb5bd;
}

/* Carousel Dots */
.carousel-dots {
  display: flex;
  justify-content: center;
  padding: 10px 0;
}

.dot {
  width: 8px;
  height: 8px;
  background-color: #ced4da;
  border-radius: 50%;
  margin: 0 4px;
  cursor: pointer;
}

.dot.active {
  background-color: #000000;
}

/* Chat Input */
.chat-input {
  padding: 12px 20px;
  background-color: #f9f9f9;
  border-top: 1px solid #e5e5e5;
  flex-shrink: 0;
}

.input-container {
  display: flex;
  align-items: center;
  background-color: #ffffff;
  border-radius: 22px;
  border: 1px solid #e5e5e5;
  transition: border-color 0.2s ease;
}

.input-container:focus-within {
  border-color: #000000;
}

.message-input {
  flex-grow: 1;
  border: none;
  outline: none;
  padding: 10px 16px;
  font-size: 15px;
  background: transparent;
  color: #333333;
}

.send-button {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background: #000000;
  color: #ffffff;
  border: none;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 4px;
  transition: background-color 0.2s ease;
}

.send-button svg {
  width: 18px;
  height: 18px;
}

.send-button:disabled {
  background-color: #ced4da;
  cursor: not-allowed;
}

/* Robot Face Button Styling */
.robot-face-btn {
  width: 70px !important;
  height: 70px !important;
  animation: robot-float 3s ease-in-out infinite,
             robot-drift 8s ease-in-out infinite;
}

.robot-face {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
}

.robot-head {
  width: 45px;
  height: 45px;
  position: relative;
  animation: robot-head-tilt 4s ease-in-out infinite alternate;
}

.robot-antenna {
  position: absolute;
  width: 2px;
  height: 8px;
  background: #ffffff;
  border-radius: 2px;
  top: -6px;
  animation: antenna-sway 2s ease-in-out infinite;
}

.robot-antenna.left {
  left: 12px;
  animation-delay: 0s;
}

.robot-antenna.right {
  right: 12px;
  animation-delay: 1s;
}

.robot-antenna::after {
  content: '';
  position: absolute;
  top: -3px;
  left: 50%;
  transform: translateX(-50%);
  width: 4px;
  height: 4px;
  background: #00ff88;
  border-radius: 50%;
  box-shadow: 0 0 8px #00ff88;
  animation: antenna-pulse 2s ease-in-out infinite;
}

.robot-face-shell {
  width: 100%;
  height: 100%;
  background: linear-gradient(145deg, #2a2a2a, #1a1a1a);
  border-radius: 12px;
  border: 1px solid #444;
  position: relative;
  box-shadow: 
    inset 0 2px 4px rgba(255, 255, 255, 0.1),
    0 4px 8px rgba(0, 0, 0, 0.3);
}

.robot-eyes {
  display: flex;
  justify-content: space-between;
  padding: 10px 8px 4px;
  position: relative;
}

.robot-eye {
  width: 10px;
  height: 10px;
  background: #00ff88;
  border-radius: 50%;
  position: relative;
  box-shadow: 0 0 8px #00ff88;
  animation: robot-blink 3s ease-in-out infinite;
}

.eye-pupil {
  position: absolute;
  width: 4px;
  height: 4px;
  background: #000;
  border-radius: 50%;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  animation: pupil-move 5s ease-in-out infinite;
}

.eye-glow {
  position: absolute;
  width: 100%;
  height: 100%;
  background: radial-gradient(circle, rgba(0, 255, 136, 0.8) 0%, transparent 70%);
  border-radius: 50%;
  animation: eye-glow-pulse 2s ease-in-out infinite;
}

.robot-mouth {
  position: absolute;
  bottom: 8px;
  left: 50%;
  transform: translateX(-50%);
  width: 20px;
  height: 8px;
  display: flex;
  flex-direction: column;
  gap: 1px;
  align-items: center;
}

.mouth-line {
  width: 12px;
  height: 1px;
  background: #00ff88;
  opacity: 0.8;
  animation: mouth-talk 1.5s ease-in-out infinite;
}

.mouth-line:nth-child(2) {
  width: 8px;
  animation-delay: 0.2s;
}

.mouth-line:nth-child(3) {
  width: 6px;
  animation-delay: 0.4s;
}

.robot-cheek-vents {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 100%;
  display: flex;
  justify-content: space-between;
  padding: 0 2px;
}

.vent {
  width: 6px;
  height: 8px;
  background: linear-gradient(to bottom, #444 0%, #222 100%);
  border-radius: 1px;
  position: relative;
  box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.5);
}

.vent::after {
  content: '';
  position: absolute;
  width: 2px;
  height: 100%;
  background: #666;
  left: 50%;
  transform: translateX(-50%);
}

.floating-particles {
  position: absolute;
  width: 100%;
  height: 100%;
  pointer-events: none;
}

.particle {
  position: absolute;
  width: 2px;
  height: 2px;
  background: #00ff88;
  border-radius: 50%;
  opacity: 0.7;
  animation: particle-float 4s ease-in-out infinite;
}

.particle:nth-child(1) { top: 20%; left: 10%; animation-delay: 0s; }
.particle:nth-child(2) { top: 80%; left: 90%; animation-delay: 0.5s; }
.particle:nth-child(3) { top: 60%; left: 20%; animation-delay: 1s; }
.particle:nth-child(4) { top: 30%; left: 85%; animation-delay: 1.5s; }
.particle:nth-child(5) { top: 90%; left: 15%; animation-delay: 2s; }
.particle:nth-child(6) { top: 15%; left: 75%; animation-delay: 2.5s; }
.particle:nth-child(7) { top: 70%; left: 80%; animation-delay: 3s; }
.particle:nth-child(8) { top: 40%; left: 5%; animation-delay: 3.5s; }

/* Robot Animations */
@keyframes robot-float {
  0%, 100% { transform: translateY(0px) rotate(0deg); }
  50% { transform: translateY(-8px) rotate(2deg); }
}

@keyframes robot-drift {
  0%, 100% { transform: translateX(0px); }
  25% { transform: translateX(3px); }
  75% { transform: translateX(-3px); }
}

@keyframes robot-head-tilt {
  0%, 100% { transform: rotate(0deg); }
  50% { transform: rotate(5deg); }
}

@keyframes antenna-sway {
  0%, 100% { transform: rotate(0deg); }
  50% { transform: rotate(15deg); }
}

@keyframes antenna-pulse {
  0%, 100% { opacity: 1; transform: translateX(-50%) scale(1); }
  50% { opacity: 0.6; transform: translateX(-50%) scale(1.2); }
}

@keyframes robot-blink {
  0%, 90%, 100% { transform: scaleY(1); }
  95% { transform: scaleY(0.1); }
}

@keyframes pupil-move {
  0%, 100% { transform: translate(-50%, -50%); }
  25% { transform: translate(-70%, -50%); }
  50% { transform: translate(-50%, -70%); }
  75% { transform: translate(-30%, -50%); }
}

@keyframes eye-glow-pulse {
  0%, 100% { opacity: 0.8; transform: scale(1); }
  50% { opacity: 1; transform: scale(1.1); }
}

@keyframes mouth-talk {
  0%, 100% { opacity: 0.8; transform: scaleX(1); }
  50% { opacity: 1; transform: scaleX(1.2); }
}

@keyframes particle-float {
  0%, 100% { 
    opacity: 0.7; 
    transform: translateY(0px) translateX(0px); 
  }
  50% { 
    opacity: 1; 
    transform: translateY(-15px) translateX(10px); 
  }
}

.robot-face-btn:hover .robot-head {
  animation-duration: 1s;
}

.robot-face-btn:hover .robot-eye {
  box-shadow: 0 0 15px #00ff88;
}

.robot-face-btn:hover .particle {
  animation-duration: 2s;
}

.robot-face-btn.active .robot-face-shell {
  background: linear-gradient(145deg, #00ff88, #00cc66);
}

.robot-face-btn.active .robot-eye {
  background: #ffffff;
  box-shadow: 0 0 15px #ffffff;
}

</style>



