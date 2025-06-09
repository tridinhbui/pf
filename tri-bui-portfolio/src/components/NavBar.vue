<template>
  <nav class="navbar" :class="{ 'navbar-scrolled': isScrolled }">
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
        <a href="#experience" class="nav-link" @click="scrollToSection('experience')">
          <span>Experience</span>
        </a>
        <a href="#awards" class="nav-link" @click="scrollToSection('awards')">
          <span>Awards</span>
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
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border-bottom: 1px solid rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
  height: 70px;
}

.navbar-scrolled {
  background: rgba(255, 255, 255, 0.98);
  box-shadow: 0 2px 20px rgba(0, 0, 0, 0.1);
}

.nav-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 70px;
}

.nav-brand {
  display: flex;
  align-items: center;
}

.brand-link {
  display: flex;
  align-items: center;
  text-decoration: none;
  color: #000000;
  font-weight: 700;
  font-size: 1.125rem;
  letter-spacing: -0.02em;
  line-height: 1;
}

.brand-text {
  margin-right: 0.5rem;
  white-space: nowrap;
}

.brand-dot {
  width: 6px;
  height: 6px;
  background: #000000;
  border-radius: 50%;
  animation: pulse-dot 2s infinite;
  flex-shrink: 0;
}

@keyframes pulse-dot {
  0%, 100% { transform: scale(1); opacity: 1; }
  50% { transform: scale(1.2); opacity: 0.7; }
}

.nav-menu {
  display: flex;
  align-items: center;
  gap: 2rem;
}

.nav-link {
  position: relative;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.75rem 1rem;
  text-decoration: none;
  color: #333333;
  font-weight: 500;
  font-size: 0.95rem;
  border-radius: 0.5rem;
  transition: all 0.3s ease;
}

.nav-link:hover {
  color: #000000;
  background: rgba(0, 0, 0, 0.05);
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 2px;
  background: #000000;
  transition: width 0.3s ease;
}

.nav-link:hover::after {
  width: 80%;
}

.contact-btn {
  background: #000000;
  color: #ffffff !important;
  border-radius: 2rem;
  padding: 0.75rem 1.5rem;
}

.contact-btn:hover {
  background: #333333;
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
}

.contact-btn::after {
  display: none;
}

.contact-icon {
  width: 16px;
  height: 16px;
  transition: transform 0.3s ease;
}

.contact-btn:hover .contact-icon {
  transform: translateX(4px);
}

.mobile-toggle {
  display: none;
  cursor: pointer;
  padding: 0.5rem;
}

.hamburger {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.hamburger span {
  width: 24px;
  height: 2px;
  background: #000000;
  transition: all 0.3s ease;
  transform-origin: center;
}

.hamburger-active span:nth-child(1) {
  transform: rotate(45deg) translate(6px, 6px);
}

.hamburger-active span:nth-child(2) {
  opacity: 0;
}

.hamburger-active span:nth-child(3) {
  transform: rotate(-45deg) translate(6px, -6px);
}

/* Mobile Styles */
@media (max-width: 768px) {
  .mobile-toggle {
    display: block;
  }

  .nav-menu {
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    background: rgba(255, 255, 255, 0.98);
    backdrop-filter: blur(10px);
    flex-direction: column;
    gap: 0;
    padding: 1rem 0;
    border-top: 1px solid rgba(0, 0, 0, 0.1);
    transform: translateY(-100%);
    opacity: 0;
    visibility: hidden;
    transition: all 0.3s ease;
  }

  .nav-menu-active {
    transform: translateY(0);
    opacity: 1;
    visibility: visible;
  }

  .nav-link {
    width: 100%;
    padding: 1rem 2rem;
    border-radius: 0;
  }

  .contact-btn {
    margin: 0.5rem 2rem;
    width: calc(100% - 4rem);
    justify-content: center;
  }
}
</style> 