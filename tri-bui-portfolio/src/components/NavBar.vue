<template>
  <nav class="navbar" :class="{ 'navbar-scrolled': isScrolled, 'navbar-hidden': props.hideNavbar }" v-show="!props.hideNavbar">
    <!-- Galaxy Background -->
    <div class="galaxy-background">
      <div class="galaxy-stars">
        <div class="star" v-for="n in 30" :key="n" :style="getStarStyle(n)"></div>
      </div>
      <div class="galaxy-particles">
        <div class="particle" v-for="n in 20" :key="n" :style="getParticleStyle(n)"></div>
      </div>
      <div class="cosmic-waves">
        <div class="wave" v-for="n in 3" :key="n" :style="{ animationDelay: `${n * 1.5}s` }"></div>
      </div>
    </div>
    
    <div class="nav-container">
      <!-- Logo/Brand -->
      <div class="nav-brand">
        <a href="#" class="brand-link">
          <span class="brand-text">TRI</span>
          <span class="brand-accent">BUI</span>
        </a>
      </div>

      <!-- Desktop Menu -->
      <div class="nav-menu" :class="{ 'nav-menu-open': isMenuOpen }">
        <a href="#background" class="nav-link">Origin</a>
        <a href="#ventures" class="nav-link">Ventures</a>
        <a href="#triangle" class="nav-link">Triangle</a>
        <a href="#mindset" class="nav-link">Mindset</a>
        <router-link to="/blog" class="nav-link">Blog</router-link>
        <a href="#contact" class="nav-link">Contact</a>
      </div>

      <!-- Mobile Menu Button -->
      <div class="mobile-menu-btn" @click="toggleMenu">
        <span class="hamburger-line" :class="{ 'active': isMenuOpen }"></span>
        <span class="hamburger-line" :class="{ 'active': isMenuOpen }"></span>
        <span class="hamburger-line" :class="{ 'active': isMenuOpen }"></span>
      </div>
    </div>
  </nav>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const props = defineProps<{
  hideNavbar?: boolean
}>()

const isScrolled = ref(false)
const isMenuOpen = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

const getStarStyle = (index: number) => {
  return {
    left: `${Math.random() * 100}%`,
    top: `${Math.random() * 100}%`,
    animationDelay: `${Math.random() * 5}s`,
    animationDuration: `${2 + Math.random() * 3}s`
  }
}

const getParticleStyle = (index: number) => {
  return {
    left: `${Math.random() * 100}%`,
    top: `${Math.random() * 100}%`,
    animationDelay: `${Math.random() * 8}s`,
    animationDuration: `${6 + Math.random() * 4}s`
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
  width: 100%;
  z-index: 1000;
  background: rgba(0, 0, 0, 0.1);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid rgba(100, 200, 255, 0.1);
  transition: all 0.3s ease;
  overflow: hidden;
}

.navbar-scrolled {
  background: rgba(0, 0, 0, 0.98);
  backdrop-filter: blur(20px);
  border-bottom-color: rgba(255, 255, 255, 0.2);
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.8);
}

/* Galaxy Background */
.galaxy-background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
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
  box-shadow: 0 0 6px rgba(255, 255, 255, 0.8);
}

@keyframes star-twinkle {
  0%, 100% { opacity: 0.3; transform: scale(1); }
  50% { opacity: 1; transform: scale(1.5); }
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
  background: radial-gradient(circle, rgba(100, 200, 255, 0.8), transparent);
  border-radius: 50%;
  animation: particle-drift infinite linear;
}

@keyframes particle-drift {
  0% { transform: translateX(-20px); opacity: 0; }
  10% { opacity: 1; }
  90% { opacity: 1; }
  100% { transform: translateX(120vw); opacity: 0; }
}

.cosmic-waves {
  position: absolute;
  width: 100%;
  height: 100%;
}

.wave {
  position: absolute;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, transparent, rgba(100, 200, 255, 0.3), transparent);
  animation: wave-flow 8s ease-in-out infinite;
}

.wave:nth-child(1) { top: 20%; }
.wave:nth-child(2) { top: 50%; }
.wave:nth-child(3) { top: 80%; }

@keyframes wave-flow {
  0%, 100% { opacity: 0; transform: translateX(-100%); }
  50% { opacity: 1; transform: translateX(100%); }
}

/* Navigation Container */
.nav-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem 2rem;
  max-width: 1200px;
  margin: 0 auto;
  position: relative;
  z-index: 10;
}

/* Brand */
.nav-brand {
  z-index: 1001;
}

.brand-link {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  text-decoration: none;
  font-size: 1.5rem;
  font-weight: 700;
  transition: all 0.3s ease;
}

.brand-text {
  color: #ffffff;
  text-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
}

.brand-accent {
  color: #64c8ff;
  text-shadow: 0 0 15px rgba(100, 200, 255, 0.8);
}

.brand-link:hover {
  transform: scale(1.05);
}

.brand-link:hover .brand-text {
  text-shadow: 0 0 20px rgba(255, 255, 255, 0.8);
}

.brand-link:hover .brand-accent {
  text-shadow: 0 0 25px rgba(100, 200, 255, 1);
}

/* Navigation Menu */
.nav-menu {
  display: flex;
  align-items: center;
  gap: 2rem;
  transition: all 0.3s ease;
}

.nav-link {
  color: rgba(255, 255, 255, 0.8);
  text-decoration: none;
  font-weight: 500;
  font-size: 0.95rem;
  padding: 0.5rem 1rem;
  border-radius: 8px;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.nav-link::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(100, 200, 255, 0.2), transparent);
  transition: left 0.5s ease;
}

.nav-link:hover::before {
  left: 100%;
}

.nav-link:hover {
  color: #ffffff;
  background: rgba(100, 200, 255, 0.1);
  box-shadow: 0 0 20px rgba(100, 200, 255, 0.3);
  text-shadow: 0 0 10px rgba(100, 200, 255, 0.8);
  transform: translateY(-2px);
}

/* Mobile Menu Button */
.mobile-menu-btn {
  display: none;
  flex-direction: column;
  gap: 4px;
  cursor: pointer;
  padding: 8px;
  z-index: 1001;
}

.hamburger-line {
  width: 25px;
  height: 3px;
  background: #ffffff;
  border-radius: 2px;
  transition: all 0.3s ease;
  box-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
}

.hamburger-line.active:nth-child(1) {
  transform: rotate(45deg) translate(7px, 7px);
  background: #64c8ff;
  box-shadow: 0 0 15px rgba(100, 200, 255, 0.8);
}

.hamburger-line.active:nth-child(2) {
  opacity: 0;
}

.hamburger-line.active:nth-child(3) {
  transform: rotate(-45deg) translate(7px, -7px);
  background: #64c8ff;
  box-shadow: 0 0 15px rgba(100, 200, 255, 0.8);
}

/* Mobile Styles */
@media (max-width: 768px) {
  .nav-container {
    padding: 1rem;
  }
  
  .mobile-menu-btn {
    display: flex;
  }
  
  .nav-menu {
    position: fixed;
    top: 0;
    right: -100%;
    width: 300px;
    height: 100vh;
    background: rgba(0, 0, 0, 0.95);
    backdrop-filter: blur(20px);
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 2rem;
    transition: right 0.3s ease;
    border-left: 1px solid rgba(100, 200, 255, 0.3);
  }
  
  .nav-menu-open {
    right: 0;
  }
  
  .nav-link {
    font-size: 1.2rem;
    padding: 1rem 2rem;
    width: 200px;
    text-align: center;
    border: 1px solid rgba(100, 200, 255, 0.2);
    background: rgba(100, 200, 255, 0.05);
  }
  
  .nav-link:hover {
    background: rgba(100, 200, 255, 0.2);
    transform: scale(1.05);
  }
}

/* Tablet Styles */
@media (max-width: 1024px) and (min-width: 769px) {
  .nav-menu {
    gap: 1.5rem;
  }
  
  .nav-link {
    font-size: 0.9rem;
    padding: 0.4rem 0.8rem;
  }
}
</style> 