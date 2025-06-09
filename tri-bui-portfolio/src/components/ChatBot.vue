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

        <!-- Quick Actions -->
        <div class="quick-actions-container">
          <div class="quick-actions-scroll">
            <div class="quick-actions-grid">
              <button 
                v-for="action in quickActions" 
                :key="action.query"
                class="quick-action"
                @click="sendQuickMessage(action.query)"
              >
                {{ action.text }}
              </button>
            </div>
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
  query: string;
}

const isOpen = ref(false)
const currentMessage = ref('')
const isTyping = ref(false)
const messagesContainer = ref<HTMLElement>()

const messages = ref<Message[]>([
  {
    id: 1,
    text: "Chào bạn! Tôi là trợ lý AI của Trí. Tôi có thể giúp gì cho bạn về các lĩnh vực như tài chính, công nghệ, và khởi nghiệp không?",
    sender: 'bot',
    time: new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' })
  }
])

const quickActions = ref<QuickAction[]>([
  { id: 1, text: "Tell me about his experience.", query: "experience" },
  { id: 2, text: "What are his technical skills?", query: "technical skills" },
  { id: 3, text: "Describe his AI/ML projects.", query: "projects" },
  { id: 4, text: "What did he do at Blackstone?", query: "blackstone" },
  { id: 5, text: "What's his primary programming language?", query: "python" },
  { id: 6, text: "How can I contact him?", query: "contact" },
])

const knowledgeBase = {
  // Greetings
  "hello": "Hello! I'm Tri's AI assistant. How can I help you today? You can ask me about his experience, technical skills, or projects.",
  "hi": "Hi there! I'm an AI assistant representing Tri. Feel free to ask me anything about his professional background.",
  "hey": "Hey! I'm here to answer your questions about Tri Bui. What would you like to know?",

  // Professional Experience & Finance
  "experience": "Tri has a background in corporate finance and investment analysis, with experience at Smithfield Foods and Blackstone (Revantage). He's skilled in financial modeling, valuation, and data analysis. Would you like to know more about a specific role?",
  "finance": "Tri's finance skills include multi-million dollar CAPEX modeling, asset valuation, and risk analysis using Python for Monte Carlo simulations. He's proficient with tools like Excel, Power BI, and SAP.",
  "blackstone": "At Blackstone (Revantage), Tri valuated a portfolio of 15 Commercial Real Estate assets worth over $350M. He also developed a Python-based Monte Carlo simulation to stress-test rent rolls, identifying and mitigating potential downside risk.",
  
  // Technical & AI/ML Skills
  "technical skills": "Tri is a full-stack developer with deep expertise in AI/ML engineering. His core competencies include Python, JavaScript (Vue.js), and system architecture. He is experienced in building end-to-end AI models. What specific area interests you?",
  "ai": "Tri has hands-on experience in AI/ML, particularly with Large Language Models (LLMs) and predictive modeling. He has fine-tuned models like Llama-2, implemented RAG pipelines for accuracy, and deployed models on cloud services like AWS. Are you interested in his 'FinBud AI' project?",
  "ml": "His Machine Learning experience includes building time-series forecasting models (Prophet), NLP tasks, and using libraries like scikit-learn, pandas, and NumPy for data analysis and modeling. He's also familiar with MLOps principles for model lifecycle management.",
  "projects": "A key project is 'FinBud AI', a personal finance assistant. It uses a fine-tuned LLM and a RAG pipeline to provide actionable insights. The backend is a serverless API on AWS Lambda. He's also built various other full-stack applications.",
  "python": "Python is one of Tri's main languages. He uses it for financial modeling (pandas, NumPy), machine learning (scikit-learn, PyTorch), and building backend services.",
  
  // Personal & Contact
  "contact": "You can reach out to Tri via the contact form on this website or connect with him on LinkedIn. The links are in the footer.",
  "about": "Tri Bui is a professional with a unique blend of finance and technology expertise. He is passionate about using AI and software development to solve complex problems. This portfolio was designed and coded by him from scratch!",
  
  // Default/Fallback
  "default": "That's an interesting question. I don't have a specific answer for that right now, but I'm constantly learning. Try asking me about Tri's experience, AI projects, or technical skills."
};

const getBotResponse = (userMessage: string): string => {
  const lowerCaseMessage = userMessage.toLowerCase();
  let bestMatch = 'default';
  let highestMatchCount = 0;

  // Simple keyword matching logic
  for (const key in knowledgeBase) {
    if (key !== 'default') {
      const keywords = key.split(' ');
      let currentMatchCount = 0;
      keywords.forEach(keyword => {
        if (lowerCaseMessage.includes(keyword)) {
          currentMatchCount++;
        }
      });
      if (currentMatchCount > highestMatchCount) {
        highestMatchCount = currentMatchCount;
        bestMatch = key;
      }
    }
  }

  // A few hardcoded checks for better accuracy
  if (lowerCaseMessage.includes('hello') || lowerCaseMessage.includes('hi') || lowerCaseMessage.includes('hey')) bestMatch = 'hello';
  if (lowerCaseMessage.includes('blackstone')) bestMatch = 'blackstone';
  if (lowerCaseMessage.includes('ai') || lowerCaseMessage.includes('ml')) bestMatch = 'ai';

  return knowledgeBase[bestMatch];
}

const toggleChat = () => {
  isOpen.value = !isOpen.value
}

watch(() => props.autoOpen, (newValue) => {
  if (newValue) {
    setTimeout(() => {
      isOpen.value = true;
    }, 500)
  }
});

const sendMessage = async () => {
  if (!currentMessage.value.trim() || isTyping.value) return
  
  const userMessage: Message = {
    id: Date.now(),
    text: currentMessage.value,
    sender: 'user',
    time: new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' })
  }
  
  messages.value.push(userMessage)
  const messageToSend = currentMessage.value;
  currentMessage.value = ''
  
  await nextTick()
  scrollToBottom()
  
  // Simulate bot response
  isTyping.value = true
  setTimeout(() => {
    const botResponseText = getBotResponse(messageToSend);
    const botResponse: Message = {
      id: Date.now(),
      text: botResponseText,
      sender: 'bot',
      time: new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' })
    }
    
    messages.value.push(botResponse)
    isTyping.value = false
    
    nextTick(() => {
      scrollToBottom()
    })
  }, 1500)
}

const sendQuickMessage = (text: string) => {
  currentMessage.value = text
  sendMessage()
}

const scrollToBottom = () => {
  if (messagesContainer.value) {
    messagesContainer.value.scrollTop = messagesContainer.value.scrollHeight
  }
}

onMounted(() => {
  if (props.autoOpen) {
    setTimeout(() => {
      isOpen.value = true;
    }, 500)
  }
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

/* Quick Actions */
.quick-actions-container {
  padding: 0 1rem;
  margin-bottom: 1rem;
}

.quick-actions-scroll {
  display: flex;
  overflow-x: auto;
  padding-bottom: 1rem; /* for scrollbar */
  scrollbar-width: thin;
  scrollbar-color: #4f4f4f #2c2c2c;
  -webkit-overflow-scrolling: touch;
}

.quick-actions-scroll::-webkit-scrollbar {
  height: 5px;
}

.quick-actions-scroll::-webkit-scrollbar-track {
  background: #2c2c2c;
  border-radius: 10px;
}

.quick-actions-scroll::-webkit-scrollbar-thumb {
  background-color: #4f4f4f;
  border-radius: 10px;
}

.quick-actions-grid {
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  height: 90px; /* Two rows of ~40px buttons + gap */
  gap: 0.5rem;
}

.quick-action {
  padding: 0.5rem 1rem;
  background-color: #3a3a3a;
  color: #e0e0e0;
  border: 1px solid #555;
  border-radius: 20px;
  cursor: pointer;
  transition: all 0.3s ease;
  font-size: 0.85rem;
  text-align: center;
  white-space: nowrap; /* Prevent line breaks */
}

.quick-action:hover {
  background-color: #4a4a4a;
  border-color: #777;
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



