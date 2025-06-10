<template>
  <div class="chatbot-container">
    <!-- Chat Button -->
    <button 
      class="chat-button"
      @click="toggleChat"
      :class="{ 'active': isOpen }"
    >
      <div class="button-icon">
        <svg v-if="!isOpen" viewBox="0 0 24 24" fill="none" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z"/>
        </svg>
        <svg v-else viewBox="0 0 24 24" fill="none" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
        </svg>
      </div>
      <div class="pulse-ring"></div>
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
  projects: "Tri has founded and developed several technology projects, most notably:\\n- **FinBud AI:** A personal finance AI assistant with over 12,000 beta users. This project uses NLP models to understand user requests and time-series forecasting algorithms to provide financial advice.\\n- **DetectAuto (PoC):** Implemented computer vision proofs of concept for quality control at Daikin, helping reduce product defect rates by 12%.",
  skills: "Tri has a diverse skill set:\\n- **Languages:** Python, JavaScript/TypeScript, SQL, R\\n- **Frameworks:** Vue.js, React, Node.js, TensorFlow, PyTorch\\n- **Infrastructure:** AWS (Lambda, S3, EC2), Docker, CI/CD\\n- **AI/ML:** Natural Language Processing (NLP), Time-Series Forecasting, LLM Fine-tuning, Computer Vision (Object Detection)\\n- **Databases:** Experience with PostgreSQL, MongoDB, and vector databases",
  philosophy: "Tri's philosophy is building sustainable ecosystems rather than individual products. He believes in 'learn fast, teach faster,' 'build systems, not barriers,' and always 'lift others as you climb.'",
  contact: "You can reach Tri via email at tbui@macalester.edu or connect via LinkedIn: linkedin.com/in/tribuidinh",
  schedule: "To schedule a meeting, you can email Tri directly with your preferred time. He'll respond as soon as possible.",
  education: "Tri graduated from Macalester College with a dual degree in Computer Science and Quantitative Economics. He was a $230K Kofi Annan Scholar and made Dean's List for all 6 semesters. He also completed an exchange program at NTU Singapore.",
  unique: "What makes Tri unique is his ability to bridge three worlds: technology, finance, and entrepreneurship. He's not just building products, but entire ecosystems that create lasting impact for the next generation."
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
  if ('speechSynthesis' in window) {
    const utterance = new SpeechSynthesisUtterance(text.replace(/<[^>]*>/g, ''));
    utterance.rate = 1.5; // Increased speed
    utterance.pitch = 1;
    utterance.volume = 0.8;
    
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
    
    speechSynthesis.speak(utterance);
  }
}

const toggleChat = () => {
  isOpen.value = !isOpen.value
}

watch(() => props.autoOpen, (newValue) => {
  if (newValue) {
    setTimeout(() => {
      isOpen.value = true;
      // Auto-speak welcome message
      setTimeout(() => {
        speakText(messages.value[0].text);
      }, 500);
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
      // Auto-speak bot response
      speakText(botResponse)
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
  padding: 16px 20px;
  background-color: #f9f9f9;
  border-bottom: 1px solid #e5e5e5;
  flex-shrink: 0;
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

</style>



