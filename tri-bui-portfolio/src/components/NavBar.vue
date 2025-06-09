<template>
  <nav class="navbar" :class="{ 'navbar-scrolled': isScrolled }">
    <!-- Galaxy Background -->
    <div class="galaxy-background">
      <div class="galaxy-stars">
        <div class="star" v-for="n in 20" :key="n" :style="getStarStyle(n)"></div>
      </div>
      <div class="galaxy-particles">
        <div class="particle" v-for="n in 15" :key="n" :style="getParticleStyle(n)"></div>
      </div>
      <div class="cosmic-waves">
        <div class="wave" v-for="n in 3" :key="n"></div>
      </div>
    </div>
    
    <div class="nav-container">
      <!-- Logo/Brand -->
      <div class="nav-brand">
        <a href="#" class="brand-link">
          <span class="brand-text">TRI BUI</span>
          <span class="brand-dot"></span>
        </a>
      </div>

      <!-- Desktop Navigation -->
      <div class="nav-menu" :class="{ 'nav-menu-active': isMobileMenuOpen }">
        <a href="#background" class="nav-link" @click="scrollToSection('background')">
          <span>Background</span>
        </a>
        <a href="#ventures" class="nav-link" @click="scrollToSection('ventures')">
          <span>Ventures</span>
        </a>
        <a href="#triangle" class="nav-link" @click="scrollToSection('triangle')">
          <span>Triangle</span>
        </a>
        <a href="#mindset" class="nav-link" @click="scrollToSection('mindset')">
          <span>Mindset</span>
        </a>
        <a href="#blog" class="nav-link" @click="scrollToSection('blog')">
          <span>Blog</span>
        </a>
        <a href="#contact" class="nav-link contact-btn" @click="scrollToSection('contact')">
          <span>Get In Touch</span>
          <svg class="contact-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"/>
          </svg>
        </a>
      </div>

      <!-- Mobile Menu Toggle -->
      <div class="mobile-toggle" @click="toggleMobileMenu">
        <div class="hamburger" :class="{ 'hamburger-active': isMobileMenuOpen }">
          <span></span>
          <span></span>
          <span></span>
        </div>
      </div>
    </div>
  </nav>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const isMobileMenuOpen = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const scrollToSection = (sectionId: string) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
  isMobileMenuOpen.value = false
}

const getStarStyle = (n: number) => {
  return {
    left: `${Math.random() * 100}%`,
    top: `${Math.random() * 100}%`,
    animationDelay: `${Math.random() * 3}s`,
    animationDuration: `${2 + Math.random() * 3}s`
  }
}

const getParticleStyle = (n: number) => {
  return {
    left: `${Math.random() * 100}%`,
    top: `${Math.random() * 100}%`,
    animationDelay: `${Math.random() * 5}s`,
    animationDuration: `${4 + Math.random() * 6}s`
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  background: rgba(0, 0, 0, 0.9);
  backdrop-filter: blur(15px);
  -webkit-backdrop-filter: blur(15px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  transition: all 0.3s ease;
  height: 80px;
  overflow: hidden;
}

.navbar-scrolled {
  background: rgba(0, 0, 0, 0.95);
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.3);
}

/* Galaxy Background */
.galaxy-background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
  overflow: hidden;
}

.galaxy-stars {
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
  animation: star-twinkle infinite ease-in-out;
  box-shadow: 0 0 6px #ffffff;
}

@keyframes star-twinkle {
  0%, 100% { opacity: 0.3; transform: scale(1); }
  50% { opacity: 1; transform: scale(1.2); }
}

.galaxy-particles {
  position: absolute;
  width: 100%;
  height: 100%;
}

.particle {
  position: absolute;
  width: 1px;
  height: 1px;
  background: rgba(100, 200, 255, 0.6);
  border-radius: 50%;
  animation: particle-drift infinite linear;
}

@keyframes particle-drift {
  0% { transform: translateX(-20px) translateY(0) scale(0); opacity: 0; }
  10% { opacity: 1; transform: scale(1); }
  90% { opacity: 1; }
  100% { transform: translateX(calc(100vw + 20px)) translateY(-10px) scale(0); opacity: 0; }
}

.cosmic-waves {
  position: absolute;
  width: 100%;
  height: 100%;
}

.wave {
  position: absolute;
  width: 200%;
  height: 2px;
  background: linear-gradient(90deg, 
    transparent 0%, 
    rgba(100, 200, 255, 0.2) 25%, 
    rgba(100, 200, 255, 0.4) 50%, 
    rgba(100, 200, 255, 0.2) 75%, 
    transparent 100%);
  animation: cosmic-wave 8s linear infinite;
}

.wave:nth-child(1) { top: 20%; animation-delay: 0s; }
.wave:nth-child(2) { top: 50%; animation-delay: -3s; }
.wave:nth-child(3) { top: 80%; animation-delay: -6s; }

@keyframes cosmic-wave {
  0% { transform: translateX(-100%); }
  100% { transform: translateX(0%); }
}

.nav-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 80px;
  position: relative;
  z-index: 10;
}

.nav-brand {
  display: flex;
  align-items: center;
}

.brand-link {
  display: flex;
  align-items: center;
  text-decoration: none;
  color: #ffffff;
  font-weight: 700;
  font-size: 1.25rem;
  letter-spacing: -0.02em;
  line-height: 1;
  transition: all 0.3s ease;
}

.brand-link:hover {
  transform: scale(1.05);
  text-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
}

.brand-text {
  margin-right: 0.5rem;
  white-space: nowrap;
  background: linear-gradient(45deg, #ffffff, #64c8ff, #ffffff);
  background-size: 200% 200%;
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: text-shimmer 3s ease-in-out infinite;
}

@keyframes text-shimmer {
  0%, 100% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
}

.brand-dot {
  width: 8px;
  height: 8px;
  background: radial-gradient(circle, #64c8ff, #ffffff);
  border-radius: 50%;
  animation: cosmic-pulse 2s infinite;
  flex-shrink: 0;
  box-shadow: 0 0 10px #64c8ff;
}

@keyframes cosmic-pulse {
  0%, 100% { 
    transform: scale(1); 
    opacity: 1;
    box-shadow: 0 0 10px #64c8ff;
  }
  50% { 
    transform: scale(1.3); 
    opacity: 0.7;
    box-shadow: 0 0 20px #64c8ff, 0 0 30px rgba(100, 200, 255, 0.3);
  }
}

.nav-menu {
  display: flex;
  align-items: center;
  gap: 1.5rem;
}

.nav-link {
  position: relative;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.75rem 1.25rem;
  text-decoration: none;
  color: rgba(255, 255, 255, 0.8);
  font-weight: 500;
  font-size: 0.95rem;
  border-radius: 0.75rem;
  transition: all 0.3s ease;
  border: 1px solid transparent;
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
}

.nav-link:hover {
  color: #ffffff;
  background: rgba(255, 255, 255, 0.1);
  border-color: rgba(100, 200, 255, 0.3);
  box-shadow: 0 4px 20px rgba(100, 200, 255, 0.2);
  transform: translateY(-2px);
}

.nav-link::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(45deg, transparent, rgba(100, 200, 255, 0.1), transparent);
  border-radius: 0.75rem;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.nav-link:hover::before {
  opacity: 1;
}

.contact-btn {
  background: linear-gradient(135deg, #000000, #333333, #000000);
  background-size: 200% 200%;
  color: #ffffff !important;
  border: 1px solid rgba(100, 200, 255, 0.3);
  animation: contact-glow 3s ease-in-out infinite;
}

.contact-btn:hover {
  background: linear-gradient(135deg, #333333, #555555, #333333);
  transform: translateY(-3px);
  box-shadow: 
    0 6px 25px rgba(0, 0, 0, 0.3),
    0 0 20px rgba(100, 200, 255, 0.4);
}

@keyframes contact-glow {
  0%, 100% { 
    background-position: 0% 50%;
    box-shadow: 0 0 15px rgba(100, 200, 255, 0.3);
  }
  50% { 
    background-position: 100% 50%;
    box-shadow: 0 0 25px rgba(100, 200, 255, 0.5);
  }
}

.contact-icon {
  width: 16px;
  height: 16px;
  transition: transform 0.3s ease;
}

.contact-btn:hover .contact-icon {
  transform: translateX(3px);
}

.mobile-toggle {
  display: none;
  cursor: pointer;
  padding: 0.5rem;
  z-index: 15;
}

.hamburger {
  display: flex;
  flex-direction: column;
  gap: 4px;
  transition: all 0.3s ease;
}

.hamburger span {
  width: 25px;
  height: 2px;
  background: #ffffff;
  border-radius: 2px;
  transition: all 0.3s ease;
  box-shadow: 0 0 5px rgba(100, 200, 255, 0.3);
}

.hamburger-active span:nth-child(1) {
  transform: rotate(45deg) translate(5px, 5px);
}

.hamburger-active span:nth-child(2) {
  opacity: 0;
}

.hamburger-active span:nth-child(3) {
  transform: rotate(-45deg) translate(7px, -6px);
}

/* Mobile Styles */
@media (max-width: 768px) {
  .navbar {
    height: 70px;
  }
  
  .nav-container {
    height: 70px;
    padding: 0 1rem;
  }
  
  .mobile-toggle {
    display: block;
  }
  
  .nav-menu {
    position: fixed;
    top: 70px;
    left: 0;
    right: 0;
    background: rgba(0, 0, 0, 0.95);
    backdrop-filter: blur(20px);
    flex-direction: column;
    gap: 0;
    padding: 2rem 1rem;
    transform: translateY(-100%);
    opacity: 0;
    visibility: hidden;
    transition: all 0.3s ease;
    border-top: 1px solid rgba(255, 255, 255, 0.1);
  }
  
  .nav-menu-active {
    transform: translateY(0);
    opacity: 1;
    visibility: visible;
  }
  
  .nav-link {
    width: 100%;
    justify-content: center;
    padding: 1rem;
    margin: 0.5rem 0;
    font-size: 1.1rem;
  }
  
  .brand-text {
    font-size: 1.1rem;
  }
  
  .brand-dot {
    width: 6px;
    height: 6px;
  }
}

/* Ultra-wide screens */
@media (min-width: 1400px) {
  .nav-container {
    max-width: 1400px;
  }
}
</style> 