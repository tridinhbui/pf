<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const mobileMenuOpen = ref(false)
const isScrolled = ref(false)

const navigation = [
  { name: 'Trang chủ', path: '/' },
  { name: 'Về tôi', path: '/about' },
  { name: 'Kinh nghiệm', path: '/experience' },
  { name: 'Dự án', path: '/projects' },
  { name: 'Tư duy lãnh đạo', path: '/thought-leadership' },
]

const navLinks = ref([
  { name: 'About', path: '/' },
  { name: 'Work', path: '/projects' },
  { name: 'Experience', path: '/experience' },
  { name: 'Contact', path: '/contact' }
])

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}

const closeMobileMenu = () => {
  mobileMenuOpen.value = false
}

// Scroll handler
const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

// Close mobile menu when route changes
onMounted(() => {
  // Close mobile menu on route change
  const unwatchRoute = route && (() => {
    mobileMenuOpen.value = false
  })

  // Cleanup on unmount
  return unwatchRoute
})

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  handleScroll() // Check initial scroll position
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <div id="app" class="min-h-screen">
    <!-- Future Navigation -->
    <nav class="nav-future" :class="{ 'nav-scrolled': isScrolled }">
      <div class="nav-container">
        <div class="nav-content">
          <!-- Logo/Brand -->

          <!-- Desktop Navigation -->
          <div class="hidden md:flex items-center space-x-8">
            <router-link v-for="link in navLinks" :key="link.path" :to="link.path" class="nav-link"
              :class="{ 'active': route.path === link.path }">
              {{ link.name }}
            </router-link>
          </div>


          <!-- Mobile Menu Button -->
          <button @click="toggleMobileMenu" class="md:hidden p-2 rounded-lg hover:bg-gray-800 transition-colors">
            <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path v-if="!mobileMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M4 6h16M4 12h16M4 18h16" />
              <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
        </div>

        <!-- Mobile Navigation -->
        <div v-if="mobileMenuOpen" class="md:hidden py-4 border-t border-gray-800">
          <div class="space-y-4">
            <router-link v-for="link in navLinks" :key="link.path" :to="link.path" @click="closeMobileMenu"
              class="block py-2 text-gray-300 hover:text-white transition-colors"
              :class="{ 'text-blue-400': route.path === link.path }">
              {{ link.name }}
            </router-link>

          </div>
        </div>
      </div>
    </nav>

    <!-- Main Content -->
    <main class="relative">
      <router-view />
    </main>

    <!-- Modern Footer -->
    <footer class="bg-gray-900 border-t border-gray-800">
      <div class="container">
        <div class="py-12">
          <div class="grid grid-2 gap-8 md:gap-12">





          </div>



        </div>
      </div>
    </footer>
  </div>
</template>

<style scoped>
@reference 'tailwindcss';
/* Navigation styles */

.nav-link {
  @apply text-gray-300 hover:text-white transition-colors duration-200 font-medium relative;
}

.nav-link.active {
  @apply text-blue-400;
}

.nav-link.active::after {
  content: '';
  position: absolute;
  bottom: -8px;
  left: 0;
  right: 0;
  height: 2px;
  background: var(--gradient-primary);
  border-radius: 1px;
}

/* Mobile menu animation */
.mobile-menu-enter-active,
.mobile-menu-leave-active {
  transition: all 0.3s ease;
}

.mobile-menu-enter-from,
.mobile-menu-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}

/* Smooth scrolling */
html {
  scroll-behavior: smooth;
}

/* Focus styles for accessibility */
.nav-link:focus,
.btn:focus {
  @apply outline-none ring-2 ring-blue-400 ring-offset-2 ring-offset-gray-900;
}
</style>
