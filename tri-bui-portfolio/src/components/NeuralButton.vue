<template>
  <button
    class="btn"
    :class="buttonClasses"
    @click="handleClick"
    @mouseenter="handleMouseEnter"
    @mouseleave="handleMouseLeave"
    ref="buttonRef"
  >
    <span class="relative z-10 flex items-center justify-center gap-2">
      <slot name="icon" />
      <slot />
    </span>
    
    <!-- Ripple effect -->
    <div 
      v-if="showRipple"
      class="absolute inset-0 rounded-lg overflow-hidden pointer-events-none"
    >
      <div 
        class="ripple"
        :style="rippleStyle"
      ></div>
    </div>
  </button>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'

interface Props {
  variant?: 'primary' | 'secondary' | 'accent' | 'outline'
  size?: 'sm' | 'md' | 'lg'
  disabled?: boolean
  loading?: boolean
  block?: boolean
}

const props = withDefaults(defineProps<Props>(), {
  variant: 'primary',
  size: 'md',
  disabled: false,
  loading: false,
  block: false
})

const emit = defineEmits<{
  click: [event: MouseEvent]
}>()

// Refs
const buttonRef = ref<HTMLButtonElement>()
const showRipple = ref(false)
const rippleStyle = ref({})

// Computed classes
const buttonClasses = computed(() => [
  `btn-${props.variant}`,
  `btn-${props.size}`,
  {
    'w-full': props.block,
    'opacity-50 cursor-not-allowed': props.disabled || props.loading,
    'pointer-events-none': props.disabled || props.loading
  }
])

// Methods
const handleClick = (event: MouseEvent) => {
  if (props.disabled || props.loading) return
  
  createRipple(event)
  emit('click', event)
}

const handleMouseEnter = () => {
  if (props.disabled || props.loading) return
  // Add hover effects here if needed
}

const handleMouseLeave = () => {
  if (props.disabled || props.loading) return
  // Remove hover effects here if needed
}

const createRipple = (event: MouseEvent) => {
  const button = buttonRef.value
  if (!button) return

  const rect = button.getBoundingClientRect()
  const size = Math.max(rect.width, rect.height)
  const x = event.clientX - rect.left - size / 2
  const y = event.clientY - rect.top - size / 2

  rippleStyle.value = {
    width: `${size}px`,
    height: `${size}px`,
    left: `${x}px`,
    top: `${y}px`,
    transform: 'scale(0)',
    animation: 'ripple-animation 0.6s ease-out'
  }

  showRipple.value = true

  setTimeout(() => {
    showRipple.value = false
  }, 600)
}
</script>

<style scoped>
@reference 'tailwindcss';
@keyframes ripple-animation {
  from {
    transform: scale(0);
    opacity: 0.6;
  }
  to {
    transform: scale(1);
    opacity: 0;
  }
}

.ripple {
  position: absolute;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.3);
  pointer-events: none;
}

/* Loading state */
.btn:disabled .loading-spinner {
  animation: spin 1s linear infinite;
}

@keyframes spin {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}
</style> 