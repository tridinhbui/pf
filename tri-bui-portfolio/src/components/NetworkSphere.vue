<template>
  <div class="network-sphere" ref="containerRef">
    <canvas ref="canvasRef"></canvas>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'
import * as THREE from 'three'

interface NetworkNode {
  position: THREE.Vector3
  velocity: THREE.Vector3
  connections: number[]
}

const containerRef = ref<HTMLElement>()
const canvasRef = ref<HTMLCanvasElement>()

let scene: THREE.Scene
let camera: THREE.PerspectiveCamera
let renderer: THREE.WebGLRenderer
let animationId: number
let nodes: NetworkNode[] = []
let nodeGeometry: THREE.SphereGeometry
let nodeMaterial: THREE.MeshBasicMaterial
let lineMaterial: THREE.LineBasicMaterial
let nodeGroup: THREE.Group
let lineGroup: THREE.Group

const nodeCount = 50
const maxConnections = 3
const maxDistance = 100

onMounted(() => {
  if (!containerRef.value || !canvasRef.value) return

  initThreeJS()
  createNodes()
  createConnections()
  animate()
  
  // Handle resize
  window.addEventListener('resize', handleResize)
  
  // Handle scroll for parallax effect
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  if (animationId) {
    cancelAnimationFrame(animationId)
  }
  
  window.removeEventListener('resize', handleResize)
  window.removeEventListener('scroll', handleScroll)
  
  if (renderer) {
    renderer.dispose()
  }
})

const initThreeJS = () => {
  if (!containerRef.value || !canvasRef.value) return

  // Scene
  scene = new THREE.Scene()
  
  // Camera
  camera = new THREE.PerspectiveCamera(
    75,
    containerRef.value.clientWidth / containerRef.value.clientHeight,
    0.1,
    1000
  )
  camera.position.z = 200
  
  // Renderer
  renderer = new THREE.WebGLRenderer({
    canvas: canvasRef.value,
    alpha: true,
    antialias: true
  })
  renderer.setSize(containerRef.value.clientWidth, containerRef.value.clientHeight)
  renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2))
  
  // Groups
  nodeGroup = new THREE.Group()
  lineGroup = new THREE.Group()
  scene.add(nodeGroup)
  scene.add(lineGroup)
  
  // Materials
  nodeMaterial = new THREE.MeshBasicMaterial({
    color: 0x00B2FF,
    transparent: true,
    opacity: 0.8
  })
  
  lineMaterial = new THREE.LineBasicMaterial({
    color: 0x00B2FF,
    transparent: true,
    opacity: 0.3
  })
  
  nodeGeometry = new THREE.SphereGeometry(1, 8, 8)
}

const createNodes = () => {
  nodes = []
  
  for (let i = 0; i < nodeCount; i++) {
    const node: NetworkNode = {
      position: new THREE.Vector3(
        (Math.random() - 0.5) * 300,
        (Math.random() - 0.5) * 300,
        (Math.random() - 0.5) * 200
      ),
      velocity: new THREE.Vector3(
        (Math.random() - 0.5) * 0.5,
        (Math.random() - 0.5) * 0.5,
        (Math.random() - 0.5) * 0.5
      ),
      connections: []
    }
    
    nodes.push(node)
    
    // Create visual node
    const mesh = new THREE.Mesh(nodeGeometry, nodeMaterial.clone())
    mesh.position.copy(node.position)
    nodeGroup.add(mesh)
  }
}

const createConnections = () => {
  // Clear existing connections
  lineGroup.clear()
  
  // Reset connections
  nodes.forEach(node => {
    node.connections = []
  })
  
  // Create new connections
  for (let i = 0; i < nodes.length; i++) {
    const nodeA = nodes[i]
    
    if (nodeA.connections.length >= maxConnections) continue
    
    for (let j = i + 1; j < nodes.length; j++) {
      const nodeB = nodes[j]
      
      if (nodeB.connections.length >= maxConnections) continue
      if (nodeA.connections.includes(j) || nodeB.connections.includes(i)) continue
      
      const distance = nodeA.position.distanceTo(nodeB.position)
      
      if (distance < maxDistance && Math.random() > 0.7) {
        nodeA.connections.push(j)
        nodeB.connections.push(i)
        
        // Create visual connection
        const points = [nodeA.position.clone(), nodeB.position.clone()]
        const geometry = new THREE.BufferGeometry().setFromPoints(points)
        const line = new THREE.Line(geometry, lineMaterial.clone())
        lineGroup.add(line)
      }
    }
  }
}

const updateConnections = () => {
  lineGroup.children.forEach((lineObject, index) => {
    const line = lineObject as THREE.Line
    const geometry = line.geometry as THREE.BufferGeometry
    const positions = geometry.attributes.position.array as Float32Array
    
    // Find the corresponding node connection
    let connectionIndex = 0
    for (let i = 0; i < nodes.length && connectionIndex <= index; i++) {
      for (let j = 0; j < nodes[i].connections.length && connectionIndex <= index; j++) {
        if (connectionIndex === index) {
          const nodeA = nodes[i]
          const nodeB = nodes[nodeA.connections[j]]
          
          positions[0] = nodeA.position.x
          positions[1] = nodeA.position.y
          positions[2] = nodeA.position.z
          positions[3] = nodeB.position.x
          positions[4] = nodeB.position.y
          positions[5] = nodeB.position.z
          
          geometry.attributes.position.needsUpdate = true
          break
        }
        connectionIndex++
      }
    }
  })
}

const animate = () => {
  animationId = requestAnimationFrame(animate)
  
  // Update node positions
  nodes.forEach((node, index) => {
    node.position.add(node.velocity)
    
    // Boundary checking
    if (Math.abs(node.position.x) > 150) node.velocity.x *= -1
    if (Math.abs(node.position.y) > 150) node.velocity.y *= -1
    if (Math.abs(node.position.z) > 100) node.velocity.z *= -1
    
    // Update visual node
    const mesh = nodeGroup.children[index] as THREE.Mesh
    mesh.position.copy(node.position)
  })
  
  // Update connections
  updateConnections()
  
  // Rotate the entire group slowly
  nodeGroup.rotation.y += 0.001
  lineGroup.rotation.y += 0.001
  
  renderer.render(scene, camera)
}

const handleResize = () => {
  if (!containerRef.value) return
  
  const width = containerRef.value.clientWidth
  const height = containerRef.value.clientHeight
  
  camera.aspect = width / height
  camera.updateProjectionMatrix()
  
  renderer.setSize(width, height)
}

const handleScroll = () => {
  const scrollY = window.scrollY
  const maxScroll = window.innerHeight * 0.25 // 25vh
  const progress = Math.min(scrollY / maxScroll, 1)
  
  // Camera dolly effect
  camera.position.z = 200 - (progress * 50)
  
  // Increase node opacity and size based on scroll
  nodeGroup.children.forEach(mesh => {
    const material = (mesh as THREE.Mesh).material as THREE.MeshBasicMaterial
    material.opacity = 0.4 + (progress * 0.6)
    mesh.scale.setScalar(1 + progress * 2)
  })
  
  // Increase line opacity
  lineGroup.children.forEach(line => {
    const material = (line as THREE.Line).material as THREE.LineBasicMaterial
    material.opacity = 0.1 + (progress * 0.4)
  })
}
</script>

<style scoped>
.network-sphere {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  overflow: hidden;
}

canvas {
  display: block;
  width: 100%;
  height: 100%;
}
</style> 