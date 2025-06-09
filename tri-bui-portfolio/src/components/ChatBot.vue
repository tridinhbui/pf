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
              <div class="message-bubble">
                {{ message.text }}
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
        <div class="quick-actions">
          <button 
            v-for="action in quickActions" 
            :key="action.id"
            class="quick-action-btn"
            @click="sendQuickMessage(action.text)"
          >
            {{ action.text }}
          </button>
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
import { ref, onMounted, nextTick } from 'vue'

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

const messages = ref<Message[]>([
  {
    id: 1,
    text: "Hi! I'm Tri's AI assistant. How can I help you today?",
    sender: 'bot',
    time: '10:30 AM'
  }
])

const quickActions = ref<QuickAction[]>([
  { id: 1, text: "About Tri's experience" },
  { id: 2, text: "View projects" },
  { id: 3, text: "Contact information" },
  { id: 4, text: "Schedule a meeting" }
])

const botResponses = [
  "Thanks for your interest! Tri has extensive experience in entrepreneurship and finance.",
  "Tri has founded multiple successful ventures including Pathwise, CF Hub, and FinBud AI.",
  "You can reach Tri at tbui@macalester.edu or connect on LinkedIn.",
  "I'd be happy to help you schedule a meeting with Tri. Please provide your preferred time.",
  "Tri specializes in fintech, mentorship platforms, and strategic consulting.",
  "Would you like to know more about any specific project or achievement?",
  "Tri is currently working as a Corporate Finance Analyst at Smithfield Foods.",
  "Feel free to ask me anything about Tri's background, projects, or how to get in touch!"
]

const toggleChat = () => {
  isOpen.value = !isOpen.value
}

const sendMessage = async () => {
  if (!currentMessage.value.trim() || isTyping.value) return
  
  const userMessage: Message = {
    id: Date.now(),
    text: currentMessage.value,
    sender: 'user',
    time: new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' })
  }
  
  messages.value.push(userMessage)
  currentMessage.value = ''
  
  await nextTick()
  scrollToBottom()
  
  // Simulate bot response
  isTyping.value = true
  setTimeout(() => {
    const botResponse: Message = {
      id: Date.now(),
      text: botResponses[Math.floor(Math.random() * botResponses.length)],
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
  // Auto-show chat after 3 seconds
  setTimeout(() => {
    if (!isOpen.value) {
      // Add a subtle pulse to draw attention
      const button = document.querySelector('.chat-button')
      button?.classList.add('attention-pulse')
      setTimeout(() => {
        button?.classList.remove('attention-pulse')
      }, 2000)
    }
  }, 3000)
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
  width: 24px;
  height: 24px;
  color: #ffffff;
  transition: transform 0.3s ease;
}

.chat-button:hover .button-icon {
  transform: rotate(10deg);
}

.pulse-ring {
  position: absolute;
  width: 100%;
  height: 100%;
  border: 2px solid #ffffff;
  border-radius: 50%;
  opacity: 0;
  transform: scale(1);
  animation: pulse-ring 2s infinite;
}

@keyframes pulse-ring {
  0% {
    transform: scale(1);
    opacity: 0.8;
  }
  100% {
    transform: scale(1.3);
    opacity: 0;
  }
}

.attention-pulse {
  animation: attention-pulse 0.5s ease-in-out 4;
}

@keyframes attention-pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.15); }
}

/* Chat Interface */
.chat-interface {
  position: absolute;
  bottom: 80px;
  right: 0;
  width: 350px;
  height: 500px;
  background: #ffffff;
  border-radius: 20px;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.2);
  display: flex;
  flex-direction: column;
  overflow: hidden;
  border: 1px solid #e0e0e0;
}

/* Header */
.chat-header {
  background: linear-gradient(135deg, #000000, #333333);
  color: #ffffff;
  padding: 20px;
  display: flex;
  align-items: center;
  gap: 15px;
}

.bot-avatar {
  position: relative;
  width: 40px;
  height: 40px;
  background: #ffffff;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
}

.status-indicator {
  position: absolute;
  bottom: 2px;
  right: 2px;
  width: 10px;
  height: 10px;
  background: #00ff00;
  border-radius: 50%;
  border: 2px solid #ffffff;
}

.bot-info h3 {
  margin: 0;
  font-size: 16px;
  font-weight: 600;
}

.bot-info p {
  margin: 0;
  font-size: 12px;
  opacity: 0.8;
}

/* Messages */
.chat-messages {
  flex: 1;
  padding: 20px;
  overflow-y: auto;
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.message {
  display: flex;
  gap: 10px;
  align-items: flex-end;
}

.message.user {
  flex-direction: row-reverse;
}

.message-avatar {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 14px;
  background: #f0f0f0;
  flex-shrink: 0;
}

.message-content {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 5px;
}

.message.user .message-content {
  align-items: flex-end;
}

.message-bubble {
  background: #f0f0f0;
  padding: 12px 16px;
  border-radius: 18px;
  max-width: 250px;
  word-wrap: break-word;
  line-height: 1.4;
}

.message.user .message-bubble {
  background: #000000;
  color: #ffffff;
}

.message-time {
  font-size: 11px;
  color: #999999;
  padding: 0 5px;
}

/* Typing Indicator */
.typing-indicator {
  background: #f0f0f0;
  padding: 12px 16px;
  border-radius: 18px;
  display: flex;
  gap: 4px;
  align-items: center;
}

.typing-dot {
  width: 6px;
  height: 6px;
  background: #999999;
  border-radius: 50%;
  animation: typing-bounce 1.4s infinite ease-in-out;
}

.typing-dot:nth-child(1) { animation-delay: 0ms; }
.typing-dot:nth-child(2) { animation-delay: 200ms; }
.typing-dot:nth-child(3) { animation-delay: 400ms; }

@keyframes typing-bounce {
  0%, 80%, 100% { transform: translateY(0); }
  40% { transform: translateY(-8px); }
}

/* Quick Actions */
.quick-actions {
  padding: 15px 20px;
  border-top: 1px solid #e0e0e0;
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.quick-action-btn {
  background: #f8f8f8;
  border: 1px solid #e0e0e0;
  border-radius: 20px;
  padding: 8px 12px;
  font-size: 12px;
  cursor: pointer;
  transition: all 0.2s ease;
}

.quick-action-btn:hover {
  background: #000000;
  color: #ffffff;
  border-color: #000000;
}

/* Input */
.chat-input {
  padding: 20px;
  border-top: 1px solid #e0e0e0;
}

.input-container {
  display: flex;
  align-items: center;
  gap: 10px;
  background: #f8f8f8;
  border-radius: 25px;
  padding: 5px;
}

.message-input {
  flex: 1;
  border: none;
  background: transparent;
  padding: 12px 15px;
  font-size: 14px;
  outline: none;
}

.send-button {
  width: 40px;
  height: 40px;
  background: #000000;
  border: none;
  border-radius: 50%;
  color: #ffffff;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s ease;
}

.send-button:hover:not(:disabled) {
  background: #333333;
  transform: scale(1.1);
}

.send-button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
  transform: none;
}

.send-button svg {
  width: 18px;
  height: 18px;
}

/* Transitions */
.chat-slide-enter-active,
.chat-slide-leave-active {
  transition: all 0.3s ease;
}

.chat-slide-enter-from,
.chat-slide-leave-to {
  opacity: 0;
  transform: translateY(20px) scale(0.95);
}

/* Responsive */
@media (max-width: 480px) {
  .chatbot-container {
    bottom: 15px;
    right: 15px;
  }
  
  .chat-interface {
    width: 320px;
    height: 450px;
    bottom: 70px;
    right: -10px;
  }
  
  .chat-button {
    width: 50px;
    height: 50px;
  }
  
  .button-icon {
    width: 20px;
    height: 20px;
  }
}
</style>



