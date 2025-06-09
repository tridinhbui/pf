<template>
  <div class="magical-effects">
    <!-- Zig Zag Lightning Bolts -->
    <div class="lightning-layer">
      <div 
        class="lightning-bolt" 
        v-for="bolt in lightningBolts" 
        :key="bolt.id"
        :style="bolt.style"
      >
        <div class="bolt-path">
          <div class="segment" v-for="n in 8" :key="n" :class="`segment-${n}`"></div>
        </div>
        <div class="bolt-glow"></div>
      </div>
    </div>

    <!-- Magical Zig Zag Trails -->
    <div class="zigzag-trails-layer">
      <div 
        class="zigzag-trail" 
        v-for="trail in zigzagTrails" 
        :key="trail.id"
        :style="trail.style"
      >
        <div class="trail-segment" v-for="n in 12" :key="n"></div>
      </div>
    </div>

    <!-- Floating Geometric Shapes -->
    <div class="geometry-layer">
      <div 
        class="geometric-shape" 
        v-for="shape in geometricShapes" 
        :key="shape.id"
        :style="shape.style"
        :class="shape.class"
      >
        <div class="shape-inner"></div>
        <div class="shape-aura"></div>
      </div>
    </div>

    <!-- Mystical Portals -->
    <div class="portals-layer">
      <div 
        class="mystical-portal" 
        v-for="portal in portals" 
        :key="portal.id"
        :style="portal.style"
      >
        <div class="portal-ring" v-for="n in 5" :key="n"></div>
        <div class="portal-center"></div>
        <div class="portal-sparks">
          <div class="spark" v-for="n in 8" :key="n"></div>
        </div>
      </div>
    </div>

    <!-- Fractal Patterns -->
    <div class="fractals-layer">
      <div 
        class="fractal-pattern" 
        v-for="fractal in fractals" 
        :key="fractal.id"
        :style="fractal.style"
      >
        <div class="fractal-branch" v-for="n in 6" :key="n" :class="`branch-${n}`">
          <div class="sub-branch" v-for="m in 3" :key="m"></div>
        </div>
      </div>
    </div>

    <!-- Energy Streams -->
    <div class="energy-streams-layer">
      <div 
        class="energy-stream" 
        v-for="stream in energyStreams" 
        :key="stream.id"
        :style="stream.style"
      >
        <div class="stream-particle" v-for="n in 20" :key="n"></div>
      </div>
    </div>

    <!-- Constellation Lines -->
    <div class="constellation-layer">
      <div 
        class="constellation" 
        v-for="constellation in constellations" 
        :key="constellation.id"
        :style="constellation.style"
      >
        <div class="star-point" v-for="n in 5" :key="n"></div>
        <div class="connection-line" v-for="n in 4" :key="n" :class="`line-${n}`"></div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

interface MagicalElement {
  id: number;
  style: Record<string, string>;
  class?: string;
}

const lightningBolts = ref<MagicalElement[]>([])
const zigzagTrails = ref<MagicalElement[]>([])
const geometricShapes = ref<MagicalElement[]>([])
const portals = ref<MagicalElement[]>([])
const fractals = ref<MagicalElement[]>([])
const energyStreams = ref<MagicalElement[]>([])
const constellations = ref<MagicalElement[]>([])

const generateLightningBolts = () => {
  for (let i = 0; i < 8; i++) {
    lightningBolts.value.push({
      id: i,
      style: {
        left: `${Math.random() * 100}%`,
        top: `${Math.random() * 100}%`,
        animationDelay: `${Math.random() * 5}s`,
        animationDuration: `${2 + Math.random() * 3}s`,
        '--bolt-color': `hsl(${180 + Math.random() * 60}, 80%, 60%)`,
        '--bolt-length': `${80 + Math.random() * 120}px`
      }
    })
  }
}

const generateZigzagTrails = () => {
  for (let i = 0; i < 12; i++) {
    zigzagTrails.value.push({
      id: i,
      style: {
        left: `${Math.random() * 100}%`,
        top: `${Math.random() * 100}%`,
        animationDelay: `${Math.random() * 8}s`,
        animationDuration: `${6 + Math.random() * 8}s`,
        '--trail-color': `hsl(${Math.random() * 360}, 70%, 50%)`,
        '--trail-width': `${100 + Math.random() * 200}px`
      }
    })
  }
}

const generateGeometricShapes = () => {
  const shapes = ['triangle', 'hexagon', 'diamond', 'star', 'pentagon']
  
  for (let i = 0; i < 15; i++) {
    const shapeType = shapes[Math.floor(Math.random() * shapes.length)]
    
    geometricShapes.value.push({
      id: i,
      class: shapeType,
      style: {
        left: `${Math.random() * 100}%`,
        top: `${Math.random() * 100}%`,
        animationDelay: `${Math.random() * 10}s`,
        animationDuration: `${8 + Math.random() * 12}s`,
        '--shape-size': `${30 + Math.random() * 60}px`,
        '--shape-color': `hsl(${Math.random() * 360}, 60%, 50%)`,
        '--rotation-speed': `${10 + Math.random() * 20}s`
      }
    })
  }
}

const generatePortals = () => {
  for (let i = 0; i < 5; i++) {
    portals.value.push({
      id: i,
      style: {
        left: `${Math.random() * 100}%`,
        top: `${Math.random() * 100}%`,
        animationDelay: `${Math.random() * 6}s`,
        animationDuration: `${12 + Math.random() * 8}s`,
        '--portal-size': `${80 + Math.random() * 120}px`,
        '--portal-color': `hsl(${250 + Math.random() * 60}, 70%, 60%)`
      }
    })
  }
}

const generateFractals = () => {
  for (let i = 0; i < 6; i++) {
    fractals.value.push({
      id: i,
      style: {
        left: `${Math.random() * 100}%`,
        top: `${Math.random() * 100}%`,
        animationDelay: `${Math.random() * 8}s`,
        animationDuration: `${15 + Math.random() * 10}s`,
        '--fractal-scale': `${0.5 + Math.random() * 1}`,
        '--fractal-color': `hsl(${Math.random() * 360}, 80%, 40%)`
      }
    })
  }
}

const generateEnergyStreams = () => {
  for (let i = 0; i < 10; i++) {
    energyStreams.value.push({
      id: i,
      style: {
        left: `${Math.random() * 100}%`,
        top: `${Math.random() * 100}%`,
        animationDelay: `${Math.random() * 4}s`,
        animationDuration: `${4 + Math.random() * 6}s`,
        '--stream-color': `hsl(${60 + Math.random() * 120}, 90%, 60%)`,
        '--stream-length': `${150 + Math.random() * 250}px`
      }
    })
  }
}

const generateConstellations = () => {
  for (let i = 0; i < 8; i++) {
    constellations.value.push({
      id: i,
      style: {
        left: `${Math.random() * 100}%`,
        top: `${Math.random() * 100}%`,
        animationDelay: `${Math.random() * 6}s`,
        animationDuration: `${10 + Math.random() * 8}s`,
        '--constellation-size': `${60 + Math.random() * 100}px`
      }
    })
  }
}

onMounted(() => {
  generateLightningBolts()
  generateZigzagTrails()
  generateGeometricShapes()
  generatePortals()
  generateFractals()
  generateEnergyStreams()
  generateConstellations()
})
</script>

<style scoped>
.magical-effects {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
  overflow: hidden;
  pointer-events: none;
}

/* Lightning Bolts */
.lightning-layer {
  position: absolute;
  width: 100%;
  height: 100%;
}

.lightning-bolt {
  position: absolute;
  animation: lightning-flash infinite ease-in-out;
}

.bolt-path {
  position: relative;
  width: var(--bolt-length);
  height: 2px;
}

.segment {
  position: absolute;
  width: calc(var(--bolt-length) / 8);
  height: 2px;
  background: var(--bolt-color);
  box-shadow: 0 0 10px var(--bolt-color);
}

.segment-1 { left: 0; transform: rotate(15deg); }
.segment-2 { left: 12.5%; transform: rotate(-20deg); }
.segment-3 { left: 25%; transform: rotate(25deg); }
.segment-4 { left: 37.5%; transform: rotate(-15deg); }
.segment-5 { left: 50%; transform: rotate(30deg); }
.segment-6 { left: 62.5%; transform: rotate(-25deg); }
.segment-7 { left: 75%; transform: rotate(20deg); }
.segment-8 { left: 87.5%; transform: rotate(-10deg); }

.bolt-glow {
  position: absolute;
  top: -10px;
  left: 0;
  width: 100%;
  height: 20px;
  background: linear-gradient(90deg, transparent, var(--bolt-color), transparent);
  opacity: 0.3;
  filter: blur(5px);
}

@keyframes lightning-flash {
  0%, 90%, 100% { opacity: 0; }
  5%, 15% { opacity: 1; transform: scale(1); }
  10% { opacity: 0.8; transform: scale(1.1); }
}

/* Zig Zag Trails */
.zigzag-trails-layer {
  position: absolute;
  width: 100%;
  height: 100%;
}

.zigzag-trail {
  position: absolute;
  animation: zigzag-flow infinite linear;
}

.trail-segment {
  position: absolute;
  width: 15px;
  height: 2px;
  background: var(--trail-color);
  opacity: 0;
  animation: trail-segment-glow infinite ease-in-out;
}

.trail-segment:nth-child(1) { left: 0; transform: rotate(30deg); animation-delay: 0s; }
.trail-segment:nth-child(2) { left: 20px; transform: rotate(-30deg); animation-delay: 0.1s; }
.trail-segment:nth-child(3) { left: 40px; transform: rotate(45deg); animation-delay: 0.2s; }
.trail-segment:nth-child(4) { left: 60px; transform: rotate(-45deg); animation-delay: 0.3s; }
.trail-segment:nth-child(5) { left: 80px; transform: rotate(30deg); animation-delay: 0.4s; }
.trail-segment:nth-child(6) { left: 100px; transform: rotate(-30deg); animation-delay: 0.5s; }
.trail-segment:nth-child(7) { left: 120px; transform: rotate(60deg); animation-delay: 0.6s; }
.trail-segment:nth-child(8) { left: 140px; transform: rotate(-60deg); animation-delay: 0.7s; }
.trail-segment:nth-child(9) { left: 160px; transform: rotate(25deg); animation-delay: 0.8s; }
.trail-segment:nth-child(10) { left: 180px; transform: rotate(-25deg); animation-delay: 0.9s; }
.trail-segment:nth-child(11) { left: 200px; transform: rotate(40deg); animation-delay: 1s; }
.trail-segment:nth-child(12) { left: 220px; transform: rotate(-40deg); animation-delay: 1.1s; }

@keyframes zigzag-flow {
  0% { transform: translateX(-100px) translateY(100vh); }
  100% { transform: translateX(100px) translateY(-100px); }
}

@keyframes trail-segment-glow {
  0%, 100% { opacity: 0; transform: scale(1) rotate(var(--segment-rotation)); }
  50% { opacity: 1; transform: scale(1.5) rotate(var(--segment-rotation)); }
}

/* Geometric Shapes */
.geometry-layer {
  position: absolute;
  width: 100%;
  height: 100%;
}

.geometric-shape {
  position: absolute;
  width: var(--shape-size);
  height: var(--shape-size);
  animation: shape-float infinite ease-in-out;
}

.shape-inner {
  width: 100%;
  height: 100%;
  border: 2px solid var(--shape-color);
  background: radial-gradient(circle, transparent 40%, var(--shape-color) 70%);
  opacity: 0.6;
  animation: shape-rotate infinite linear;
  animation-duration: var(--rotation-speed);
}

.shape-aura {
  position: absolute;
  top: -10px;
  left: -10px;
  right: -10px;
  bottom: -10px;
  border: 1px solid var(--shape-color);
  opacity: 0.3;
  animation: aura-pulse infinite ease-in-out;
}

.triangle .shape-inner {
  clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
}

.hexagon .shape-inner {
  clip-path: polygon(25% 0%, 75% 0%, 100% 50%, 75% 100%, 25% 100%, 0% 50%);
}

.diamond .shape-inner {
  clip-path: polygon(50% 0%, 100% 50%, 50% 100%, 0% 50%);
}

.star .shape-inner {
  clip-path: polygon(50% 0%, 61% 35%, 98% 35%, 68% 57%, 79% 91%, 50% 70%, 21% 91%, 32% 57%, 2% 35%, 39% 35%);
}

.pentagon .shape-inner {
  clip-path: polygon(50% 0%, 100% 38%, 82% 100%, 18% 100%, 0% 38%);
}

@keyframes shape-float {
  0%, 100% { 
    transform: translateY(0px) translateX(0px) scale(1); 
    opacity: 0.6;
  }
  25% { 
    transform: translateY(-30px) translateX(20px) scale(1.1); 
    opacity: 0.8;
  }
  50% { 
    transform: translateY(-15px) translateX(-15px) scale(0.9); 
    opacity: 1;
  }
  75% { 
    transform: translateY(-40px) translateX(25px) scale(1.2); 
    opacity: 0.7;
  }
}

@keyframes shape-rotate {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

@keyframes aura-pulse {
  0%, 100% { 
    opacity: 0.1; 
    transform: scale(1); 
  }
  50% { 
    opacity: 0.5; 
    transform: scale(1.3); 
  }
}

/* Mystical Portals */
.portals-layer {
  position: absolute;
  width: 100%;
  height: 100%;
}

.mystical-portal {
  position: absolute;
  width: var(--portal-size);
  height: var(--portal-size);
  animation: portal-pulse infinite ease-in-out;
}

.portal-ring {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border: 1px solid var(--portal-color);
  border-radius: 50%;
  opacity: 0;
  animation: portal-ring-expand infinite ease-out;
}

.portal-ring:nth-child(1) { animation-delay: 0s; }
.portal-ring:nth-child(2) { animation-delay: 0.5s; }
.portal-ring:nth-child(3) { animation-delay: 1s; }
.portal-ring:nth-child(4) { animation-delay: 1.5s; }
.portal-ring:nth-child(5) { animation-delay: 2s; }

.portal-center {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 30%;
  height: 30%;
  background: radial-gradient(circle, var(--portal-color), transparent);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  animation: portal-core-glow infinite ease-in-out;
}

.portal-sparks {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 100%;
  height: 100%;
  transform: translate(-50%, -50%);
}

.spark {
  position: absolute;
  width: 3px;
  height: 3px;
  background: var(--portal-color);
  border-radius: 50%;
  opacity: 0;
  animation: spark-dance infinite ease-in-out;
}

.spark:nth-child(1) { top: 0; left: 50%; animation-delay: 0s; }
.spark:nth-child(2) { top: 15%; right: 15%; animation-delay: 0.2s; }
.spark:nth-child(3) { top: 50%; right: 0; animation-delay: 0.4s; }
.spark:nth-child(4) { bottom: 15%; right: 15%; animation-delay: 0.6s; }
.spark:nth-child(5) { bottom: 0; left: 50%; animation-delay: 0.8s; }
.spark:nth-child(6) { bottom: 15%; left: 15%; animation-delay: 1s; }
.spark:nth-child(7) { top: 50%; left: 0; animation-delay: 1.2s; }
.spark:nth-child(8) { top: 15%; left: 15%; animation-delay: 1.4s; }

@keyframes portal-pulse {
  0%, 100% { transform: scale(1); opacity: 0.7; }
  50% { transform: scale(1.1); opacity: 1; }
}

@keyframes portal-ring-expand {
  0% { 
    transform: scale(0.5); 
    opacity: 1; 
  }
  100% { 
    transform: scale(2); 
    opacity: 0; 
  }
}

@keyframes portal-core-glow {
  0%, 100% { opacity: 0.5; transform: translate(-50%, -50%) scale(1); }
  50% { opacity: 1; transform: translate(-50%, -50%) scale(1.2); }
}

@keyframes spark-dance {
  0%, 100% { 
    opacity: 0; 
    transform: translateX(0) translateY(0) scale(1); 
  }
  25% { 
    opacity: 1; 
    transform: translateX(20px) translateY(-20px) scale(1.5); 
  }
  50% { 
    opacity: 0.8; 
    transform: translateX(-15px) translateY(-30px) scale(1.2); 
  }
  75% { 
    opacity: 1; 
    transform: translateX(25px) translateY(-10px) scale(1.8); 
  }
}

/* Energy Streams */
.energy-streams-layer {
  position: absolute;
  width: 100%;
  height: 100%;
}

.energy-stream {
  position: absolute;
  width: var(--stream-length);
  height: 2px;
  animation: stream-flow infinite linear;
}

.stream-particle {
  position: absolute;
  width: 4px;
  height: 4px;
  background: var(--stream-color);
  border-radius: 50%;
  opacity: 0;
  animation: particle-stream infinite ease-in-out;
}

.stream-particle:nth-child(1) { left: 5%; animation-delay: 0s; }
.stream-particle:nth-child(2) { left: 10%; animation-delay: 0.1s; }
.stream-particle:nth-child(3) { left: 15%; animation-delay: 0.2s; }
.stream-particle:nth-child(4) { left: 20%; animation-delay: 0.3s; }
.stream-particle:nth-child(5) { left: 25%; animation-delay: 0.4s; }
.stream-particle:nth-child(6) { left: 30%; animation-delay: 0.5s; }
.stream-particle:nth-child(7) { left: 35%; animation-delay: 0.6s; }
.stream-particle:nth-child(8) { left: 40%; animation-delay: 0.7s; }
.stream-particle:nth-child(9) { left: 45%; animation-delay: 0.8s; }
.stream-particle:nth-child(10) { left: 50%; animation-delay: 0.9s; }
.stream-particle:nth-child(11) { left: 55%; animation-delay: 1s; }
.stream-particle:nth-child(12) { left: 60%; animation-delay: 1.1s; }
.stream-particle:nth-child(13) { left: 65%; animation-delay: 1.2s; }
.stream-particle:nth-child(14) { left: 70%; animation-delay: 1.3s; }
.stream-particle:nth-child(15) { left: 75%; animation-delay: 1.4s; }
.stream-particle:nth-child(16) { left: 80%; animation-delay: 1.5s; }
.stream-particle:nth-child(17) { left: 85%; animation-delay: 1.6s; }
.stream-particle:nth-child(18) { left: 90%; animation-delay: 1.7s; }
.stream-particle:nth-child(19) { left: 95%; animation-delay: 1.8s; }
.stream-particle:nth-child(20) { left: 100%; animation-delay: 1.9s; }

@keyframes stream-flow {
  0% { transform: translateX(-200px) translateY(100vh) rotate(45deg); }
  100% { transform: translateX(200px) translateY(-100px) rotate(45deg); }
}

@keyframes particle-stream {
  0%, 100% { 
    opacity: 0; 
    transform: translateY(0) scale(1); 
    box-shadow: 0 0 5px var(--stream-color);
  }
  50% { 
    opacity: 1; 
    transform: translateY(-10px) scale(1.5); 
    box-shadow: 0 0 15px var(--stream-color);
  }
}

/* Responsive */
@media (max-width: 768px) {
  .lightning-bolt { --bolt-length: 50px !important; }
  .zigzag-trail { --trail-width: 80px !important; }
  .geometric-shape { --shape-size: 20px !important; }
  .mystical-portal { --portal-size: 60px !important; }
  .energy-stream { --stream-length: 100px !important; }
}

/* Reduce motion */
@media (prefers-reduced-motion: reduce) {
  .lightning-bolt, .zigzag-trail, .geometric-shape, 
  .mystical-portal, .energy-stream, .constellation {
    animation: none !important;
  }
  
  .lightning-bolt *, .zigzag-trail *, .geometric-shape *, 
  .mystical-portal *, .energy-stream *, .constellation * {
    animation: none !important;
  }
}
</style> 