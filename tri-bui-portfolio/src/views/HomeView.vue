<template>
  <div class="portfolio">
    <!-- Animated Background -->
    <AnimatedBackground />
    
    <!-- Mystical Overlay Effects -->
    <div class="mystical-overlay">
      <!-- Floating Magical Shapes -->
      <div class="magical-shapes-layer">
        <div class="magical-shape diamond-shape" v-for="n in 8" :key="`diamond-${n}`"></div>
        <div class="magical-shape triangle-shape" v-for="n in 6" :key="`triangle-${n}`"></div>
        <div class="magical-shape hexagon-shape" v-for="n in 5" :key="`hexagon-${n}`"></div>
        <div class="magical-shape star-shape" v-for="n in 7" :key="`star-${n}`"></div>
      </div>

      <!-- Particle Trails -->
      <div class="particle-trails-layer">
        <div class="particle-trail" v-for="n in 12" :key="`trail-${n}`">
          <div class="trail-dot" v-for="m in 8" :key="m"></div>
        </div>
      </div>

      <!-- Energy Waves -->
      <div class="energy-waves-layer">
        <div class="energy-wave" v-for="n in 6" :key="`wave-${n}`"></div>
      </div>
    </div>
    
    <!-- Navigation Bar -->
    <NavBar />
    
    <!-- Magnetic Cursor -->
    <MagneticCursor />
    
    <!-- Hero Section -->
    <section class="section hero-section">
      <div class="container">
        <div class="hero-content">
          <!-- Professional Background Pattern -->
          <div class="background-pattern" ref="backgroundRef"></div>

          <!-- Status Badge -->
          <div class="status-badge floating-element" ref="statusRef">
            <div class="status-dot"></div>
            <span>Available for opportunities</span>
          </div>

          <!-- Main Title -->
          <div class="hero-title-wrapper floating-element" ref="heroTitleRef">
            <h1 class="hero-title professional-title cosmic-text">
              <span class="title-main glitch-text" data-text="I don't just build startups.">I don't just build startups.</span>
              <br>
              <span class="title-sub strong-emphasis typewriter-text">I build ecosystems.</span>
            </h1>
            <p class="hero-subtitle professional-subtitle">
              I'm a strategist and builder focused on empowering the next generation with platforms, tools, and meaningful mentorship.
            </p>
                    </div>

          <!-- NEXBOT Robot Section -->
          <div class="nexbot-section floating-element" ref="nexbotRef">
            <SplineRobot />
          </div>

          <!-- Launch Navigation -->
          <div class="hero-nav" ref="heroNavRef">
            <a href="#background" class="nav-link shimmer-effect">Background</a>
            <a href="#ventures" class="nav-link shimmer-effect">Ventures</a>
            <a href="#triangle" class="nav-link shimmer-effect">Triangle</a>
            <a href="#mindset" class="nav-link shimmer-effect">Mindset</a>
            <a href="#blog" class="nav-link shimmer-effect">Blog</a>
            <a href="#contact" class="nav-link shimmer-effect">Contact</a>
          </div>
        </div>
      </div>
    </section>

    <!-- Origin Story Section -->
    <section class="section origin-section" id="background">
      <!-- Section Planets -->
      <div class="section-planets">
        <div class="planet planet-1">
          <div class="planet-ring"></div>
          <div class="planet-moon"></div>
        </div>
        <div class="planet planet-2">
          <div class="planet-atmosphere"></div>
        </div>
        <div class="orbital-path">
          <div class="orbiting-object"></div>
        </div>
      </div>
      
      <div class="container">
        <div class="section-header">
          <h2 class="section-title" ref="originTitleRef">Background</h2>
          <p class="section-subtitle">The foundation that shaped my entrepreneurial journey</p>
        </div>
        
        <div class="origin-content">
          <div class="origin-grid">
            <div class="origin-item" ref="originItem1">
              <div class="origin-label">Launch vector</div>
              <div class="origin-value">Hanoi ➜ Singapore (NTU exchange) ➜ Minnesota (Macalester) ➜ Virginia (Smithfield HQ)</div>
            </div>
            <div class="origin-item" ref="originItem2">
              <div class="origin-label">Thrusters</div>
              <div class="origin-value">Dual‑core B.A. in Computer Science + Quantitative Economics</div>
            </div>
            <div class="origin-item" ref="originItem3">
              <div class="origin-label">Fuel</div>
              <div class="origin-value"><strong>$230K Kofi Annan Scholarship</strong> · Dean's List 6/6 semesters</div>
            </div>
            <div class="origin-item" ref="originItem4">
              <div class="origin-label">Current orbit</div>
              <div class="origin-value">Corporate Finance Analyst, <strong>Smithfield Foods</strong> – modelling CAPEX, optimizing $1B debt stack, and steering scenario sims.</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Prime Directives Section -->
    <section class="section directives-section" id="directives">
      <div class="container">
        <div class="section-header">
          <h2 class="section-title" ref="directivesTitleRef">Core Principles</h2>
          <p class="section-subtitle">The values that drive everything I build</p>
        </div>
        
                 <div class="directives-grid" ref="directivesRef">
           <div class="directive-card magnetic-target hover-lift morphing-card glow-on-hover breathing-animation" v-for="directive in directives" :key="directive.num">
             <div class="directive-number floating-number">{{ directive.num }}</div>
             <div class="directive-content">
               <h3 class="directive-title">{{ directive.title }}</h3>
               <p class="directive-description">{{ directive.manifestation }}</p>
             </div>
             <div class="card-glow"></div>
             <div class="card-particles">
               <div class="card-particle" v-for="n in 5" :key="n"></div>
             </div>
           </div>
         </div>
      </div>
    </section>

    <!-- Constellations Section -->
    <section class="section constellations-section" id="ventures">
      <!-- Section Cosmic Elements -->
      <div class="section-cosmos">
        <div class="cosmic-nebula"></div>
        <div class="planet planet-3">
          <div class="planet-glow"></div>
          <div class="asteroid-belt">
            <div class="asteroid" v-for="n in 8" :key="n"></div>
          </div>
        </div>
        <div class="space-station">
          <div class="station-module" v-for="n in 4" :key="n"></div>
        </div>
      </div>
      
      <div class="container">
        <div class="section-header">
          <h2 class="section-title" ref="constellationsTitleRef">Ventures</h2>
          <p class="section-subtitle">Companies and platforms I've founded to empower the next generation</p>
        </div>
        
                 <div class="constellations-grid" ref="constellationsRef">
           <div class="constellation-card magnetic-target hover-lift morphing-card stellar-card ripple-effect magnetic-field" v-for="venture in ventures" :key="venture.name">
             <div class="card-header">
               <h3 class="venture-name glowing-text">{{ venture.name }}</h3>
               <div class="venture-meta">
                 <span class="venture-year pulse-badge">{{ venture.year }}</span>
                 <span class="venture-role">{{ venture.role }}</span>
               </div>
             </div>
             <div class="card-body">
               <div class="impact-metric animated-metric">{{ venture.impact }}</div>
             </div>
             <div class="stellar-glow"></div>
             <div class="constellation-lines">
               <div class="line" v-for="n in 3" :key="n"></div>
             </div>
           </div>
         </div>
      </div>
    </section>

    <!-- Entrepreneurship Triangle Section -->
    <section class="section triangle-section" id="triangle">
      <!-- Section Cosmic Elements -->
      <div class="section-cosmos">
        <div class="cosmic-nebula"></div>
        <div class="planet planet-4">
          <div class="planet-glow"></div>
        </div>
      </div>
      
      <div class="container">
        <div class="section-header">
          <h2 class="section-title" ref="triangleTitleRef">The Entrepreneurship Triangle</h2>
          <p class="section-subtitle">Where Tech, Finance, and Marketing converge to create innovation</p>
        </div>
        
        <div class="triangle-container" ref="triangleRef">
          <!-- The Triangle -->
          <div class="entrepreneurship-triangle">
            <!-- Triangle Lines -->
            <svg class="triangle-svg" viewBox="0 0 400 346" fill="none">
              <path d="M200 50 L350 300 L50 300 Z" stroke="#000000" stroke-width="2" fill="none"/>
              <path d="M200 50 L200 300" stroke="#000000" stroke-width="1" stroke-dasharray="5,5" opacity="0.5"/>
              <path d="M125 175 L275 175" stroke="#000000" stroke-width="1" stroke-dasharray="5,5" opacity="0.5"/>
              <path d="M162.5 237.5 L237.5 237.5" stroke="#000000" stroke-width="1" stroke-dasharray="5,5" opacity="0.5"/>
            </svg>
            
            <!-- Vertices -->
            <div class="vertex tech-vertex" data-skill="tech">
              <div class="vertex-icon">💻</div>
              <div class="vertex-label">TECH</div>
              <div class="vertex-description">Full-stack development, AI/ML, System architecture</div>
            </div>
            
            <div class="vertex finance-vertex" data-skill="finance">
              <div class="vertex-icon">📊</div>
              <div class="vertex-label">FINANCE</div>
              <div class="vertex-description">Corporate finance, Investment analysis, Risk modeling</div>
            </div>
            
            <div class="vertex marketing-vertex" data-skill="marketing">
              <div class="vertex-icon">🎯</div>
              <div class="vertex-label">MARKETING</div>
              <div class="vertex-description">Growth hacking, Brand strategy, Customer acquisition</div>
            </div>
            
            <!-- Center - Entrepreneurship -->
            <div class="center-point" data-core="entrepreneurship">
              <div class="center-icon">🚀</div>
              <div class="center-label">ENTREPRENEURSHIP</div>
              <div class="center-description">Building ecosystems that empower the next generation</div>
              <div class="energy-pulse"></div>
            </div>
            
            <!-- Connection Lines -->
            <div class="connection-lines">
              <div class="line tech-to-center"></div>
              <div class="line finance-to-center"></div>
              <div class="line marketing-to-center"></div>
            </div>
          </div>
          
          <!-- Skills Breakdown -->
          <div class="skills-breakdown">
            <div class="skill-category tech-skills">
              <h3>Technology Stack</h3>
              <ul>
                <li>Vue.js, React, Node.js</li>
                <li>Python, TensorFlow, AWS</li>
                <li>Microservices Architecture</li>
                <li>Database Design & Optimization</li>
              </ul>
            </div>
            
            <div class="skill-category finance-skills">
              <h3>Financial Expertise</h3>
              <ul>
                <li>CAPEX Modeling & Analysis</li>
                <li>Monte Carlo Simulations</li>
                <li>Private Equity Valuation</li>
                <li>Risk Management</li>
              </ul>
            </div>
            
            <div class="skill-category marketing-skills">
              <h3>Growth & Marketing</h3>
              <ul>
                <li>User Acquisition Strategy</li>
                <li>Product-Market Fit</li>
                <li>Mentorship & Education</li>
                <li>Community Building</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Business Mindset Section -->
    <section class="section mindset-section" id="mindset">
      <div class="container">
        <div class="section-header">
          <h2 class="section-title" ref="mindsetTitleRef">Business & Entrepreneurship Mindset</h2>
          <p class="section-subtitle">Core principles that drive innovation and sustainable growth</p>
        </div>
        
        <div class="mindset-grid" ref="mindsetRef">
          <div class="mindset-card magnetic-target hover-lift morphing-card" v-for="mindset in businessMindset" :key="mindset.id">
            <div class="mindset-icon">{{ mindset.icon }}</div>
            <div class="mindset-content">
              <h3 class="mindset-title">{{ mindset.title }}</h3>
              <p class="mindset-description">{{ mindset.description }}</p>
              <div class="mindset-example">
                <strong>Applied:</strong> {{ mindset.example }}
              </div>
            </div>
            <div class="card-glow"></div>
          </div>
        </div>
      </div>
    </section>

    <!-- Blog Section -->
    <section class="section blog-section" id="blog">
      <div class="container">
        <div class="section-header">
          <h2 class="section-title" ref="blogTitleRef">Insights & Thoughts</h2>
          <p class="section-subtitle">Sharing knowledge on entrepreneurship, technology, and building the future</p>
        </div>
        
        <div class="blog-grid" ref="blogRef">
          <div class="blog-card magnetic-target hover-lift morphing-card" v-for="post in blogPosts" :key="post.id">
            <div class="blog-meta">
              <span class="blog-category">{{ post.category }}</span>
              <span class="blog-date">{{ post.date }}</span>
            </div>
            <div class="blog-content">
              <h3 class="blog-title">{{ post.title }}</h3>
              <p class="blog-excerpt">{{ post.excerpt }}</p>
              <div class="blog-tags">
                <span class="tag" v-for="tag in post.tags" :key="tag">{{ tag }}</span>
              </div>
            </div>
            <div class="blog-footer">
              <span class="read-time">{{ post.readTime }} min read</span>
              <a href="#" class="read-more">Read More →</a>
            </div>
            <div class="card-glow"></div>
          </div>
        </div>
        
        <div class="blog-link">
          <a href="/blog" class="elegant-link magnetic-target">
            <span>View all articles</span>
            <span class="link-arrow">→</span>
          </a>
        </div>
      </div>
    </section>

    <!-- Accolades Section -->
    <section class="section accolades-section" id="awards">
      <div class="container">
        <div class="section-header">
          <h2 class="section-title" ref="accoladesTitleRef">Awards & Recognition</h2>
          <p class="section-subtitle">Recognition for entrepreneurial impact and academic excellence</p>
        </div>
        
        <div class="accolades-timeline" ref="accoladesRef">
          <div class="timeline-item magnetic-target" v-for="accolade in accolades" :key="accolade.title">
            <div class="timeline-year">{{ accolade.year }}</div>
            <div class="timeline-content">
              <h3 class="accolade-title">{{ accolade.title }}</h3>
              <div class="accolade-achievement">{{ accolade.achievement }}</div>
            </div>
          </div>
        </div>

        <div class="trophy-link">
          <a href="/trophies" class="elegant-link magnetic-target">
            <span>Full trophy cabinet</span>
            <span class="link-arrow">→</span>
          </a>
        </div>
      </div>
    </section>

    <!-- Professional Orbits Section -->
    <section class="section orbits-section" id="experience">
      <div class="container">
        <div class="section-header">
          <h2 class="section-title" ref="orbitsTitleRef">Professional Experience</h2>
          <p class="section-subtitle">Corporate roles building expertise in finance, strategy, and technology</p>
        </div>
        
        <div class="orbits-grid" ref="orbitsRef">
          <div class="orbit-card magnetic-target" v-for="orbit in orbits" :key="orbit.org">
            <div class="orbit-header">
              <h3 class="orbit-org">{{ orbit.org }}</h3>
              <span class="orbit-year">{{ orbit.year }}</span>
            </div>
            <div class="orbit-content">
              <p class="orbit-contribution">{{ orbit.contribution }}</p>
              <div class="orbit-tech">
                <span class="tech-label">Tech Stack:</span>
                <span class="tech-list">{{ orbit.tech }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Future Trajectory Section -->
    <section class="section trajectory-section" id="trajectory">
      <div class="container">
        <div class="section-header">
          <h2 class="section-title" ref="trajectoryTitleRef">What's Next</h2>
          <p class="section-subtitle">Upcoming ventures and initiatives in development</p>
        </div>
        
        <div class="trajectory-grid" ref="trajectoryRef">
          <div class="trajectory-card magnetic-target" v-for="item in trajectory" :key="item.num">
            <div class="trajectory-number">{{ item.num }}</div>
            <div class="trajectory-content">
              <h3 class="trajectory-title">{{ item.title }}</h3>
              <p class="trajectory-description">{{ item.description }}</p>
            </div>
          </div>
        </div>

        <div class="roadmap-link">
          <a href="/stellarchart" class="elegant-link magnetic-target">
            <span>Detailed roadmap</span>
            <span class="link-arrow">→</span>
          </a>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section class="section contact-section" id="contact">
      <div class="container">
        <div class="contact-content">
          <h2 class="section-title" ref="contactTitleRef">Get In Touch</h2>
          
          <div class="contact-cta">
            <p class="contact-description">
              Ready to build something amazing together? Let's connect and explore opportunities to create meaningful impact.
            </p>
            <div class="contact-buttons">
              <a href="mailto:tbui@macalester.edu" class="contact-btn primary">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 4.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path>
                </svg>
                Send Email
              </a>
              <a href="https://linkedin.com/in/tribuidinh" class="contact-btn secondary" target="_blank" rel="noopener noreferrer">
                <svg viewBox="0 0 24 24" fill="currentColor">
                  <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
                </svg>
                Connect on LinkedIn
              </a>
            </div>
          </div>

          <div class="quote-section" ref="quoteRef">
            <blockquote class="elegant-quote">
              "Don't just scale products. Scale possibility."
            </blockquote>
          </div>
        </div>
      </div>
    </section>

    <!-- Chatbot -->
    <ChatBot />

    <!-- Footer Section -->
    <footer class="footer-section">
      <div class="container">
        <div class="footer-content">
          <div class="footer-grid">
            <!-- Brand Column -->
            <div class="footer-brand">
              <h3 class="footer-logo">TRI BUI</h3>
              <p class="footer-description">
                Building ecosystems, empowering entrepreneurs, scaling possibility.
              </p>
                             <div class="footer-social">
                 <a href="https://linkedin.com/in/tribuidinh" class="social-link" target="_blank" rel="noopener noreferrer">
                   <svg viewBox="0 0 24 24" fill="currentColor">
                     <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
                   </svg>
                 </a>
                 <a href="mailto:tbui@macalester.edu" class="social-link" rel="noopener noreferrer">
                   <svg viewBox="0 0 24 24" fill="none" stroke="currentColor">
                     <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 4.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path>
                   </svg>
                 </a>
                 <a href="https://github.com/tribuidinh" class="social-link" target="_blank" rel="noopener noreferrer">
                   <svg viewBox="0 0 24 24" fill="currentColor">
                     <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
                   </svg>
                 </a>
               </div>
            </div>

            <!-- Quick Links -->
            <div class="footer-links">
              <h4 class="footer-heading">Quick Links</h4>
              <ul class="footer-list">
                <li><a href="#background" class="footer-link">Background</a></li>
                <li><a href="#ventures" class="footer-link">Ventures</a></li>
                <li><a href="#experience" class="footer-link">Experience</a></li>
                <li><a href="#awards" class="footer-link">Awards</a></li>
              </ul>
            </div>

            <!-- Contact Info -->
            <div class="footer-contact">
              <h4 class="footer-heading">Get In Touch</h4>
              <div class="contact-item">
                <span class="contact-label">Email:</span>
                <a href="mailto:tbui@macalester.edu" class="contact-link">tbui@macalester.edu</a>
              </div>
              <div class="contact-item">
                <span class="contact-label">Location:</span>
                <span class="contact-text">Virginia, USA</span>
              </div>
              <div class="contact-item">
                <span class="contact-label">Status:</span>
                <span class="contact-text">Available for opportunities</span>
              </div>
            </div>
          </div>

          <div class="footer-bottom">
            <div class="footer-divider"></div>
            <div class="footer-bottom-content">
              <p class="footer-copyright">
                © {{ new Date().getFullYear() }} Tri Bui. All rights reserved.
              </p>
              <p class="footer-quote">
                "Building the future, one ecosystem at a time."
              </p>
            </div>
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import MagneticCursor from '@/components/MagneticCursor.vue'
import NavBar from '@/components/NavBar.vue'
import AnimatedBackground from '@/components/AnimatedBackground.vue'
import SplineRobot from '@/components/SplineRobot.vue'
import ChatBot from '@/components/ChatBot.vue'

gsap.registerPlugin(ScrollTrigger)

// Refs for animations
const statusRef = ref<HTMLElement>()
const heroTitleRef = ref<HTMLElement>()

const heroNavRef = ref<HTMLElement>()
const nexbotRef = ref<HTMLElement>()
const splineRef = ref<HTMLElement>()
const particlesRef = ref<HTMLElement>()
const originTitleRef = ref<HTMLElement>()
const originItem1 = ref<HTMLElement>()
const originItem2 = ref<HTMLElement>()
const originItem3 = ref<HTMLElement>()
const originItem4 = ref<HTMLElement>()
const directivesTitleRef = ref<HTMLElement>()
const directivesRef = ref<HTMLElement>()
const constellationsTitleRef = ref<HTMLElement>()
const constellationsRef = ref<HTMLElement>()
const triangleTitleRef = ref<HTMLElement>()
const triangleRef = ref<HTMLElement>()
const mindsetTitleRef = ref<HTMLElement>()
const mindsetRef = ref<HTMLElement>()
const blogTitleRef = ref<HTMLElement>()
const blogRef = ref<HTMLElement>()
const accoladesTitleRef = ref<HTMLElement>()
const accoladesRef = ref<HTMLElement>()
const orbitsTitleRef = ref<HTMLElement>()
const orbitsRef = ref<HTMLElement>()
const trajectoryTitleRef = ref<HTMLElement>()
const trajectoryRef = ref<HTMLElement>()
const contactTitleRef = ref<HTMLElement>()
const contactRef = ref<HTMLElement>()
const quoteRef = ref<HTMLElement>()

// Data
const directives = ref([
  {
    num: "01",
    title: "Learn fast → teach faster",
    manifestation: "300+ hours mentoring, guest‑lecturing at 4 Vietnamese HS incubators"
  },
  {
    num: "02", 
    title: "Build systems → not silos",
    manifestation: "Architected FinBud.microservices (Node+Python, 9 modular lambdas)"
  },
  {
    num: "03",
    title: "Ambition → with empathy", 
    manifestation: "Bootstrapped Esmart Solution, profit‑sharing 20 % w/ partner SMEs"
  },
  {
    num: "04",
    title: "Lift others → while you climb",
    manifestation: "Pathwise alumni placed at Amazon, Deloitte, Credit Suisse"
  }
])

const ventures = ref([
  {
    name: "Pathwise",
    year: "2021",
    role: "Founder",
    impact: "A mentorship platform helping students land top tech & consulting jobs through 1-on-1 coaching and guided curriculum. 118 mentees with 71% internship success rate."
  },
  {
    name: "CF Hub", 
    year: "2021",
    role: "Founder",
    impact: "A finance bootcamp and network for Gen Z to master investment, financial modeling, and market intuition. Generated significant impact in financial literacy."
  },
  {
    name: "YoungPreneur Academy",
    year: "2021", 
    role: "Founder",
    impact: "Entrepreneurship education program that trained 220 students, produced 46 national competition finalists, and secured $35K in prize pools."
  },
  {
    name: "FinBud AI",
    year: "2022",
    role: "Co-founder",
    impact: "Personal finance AI assistant with 12K beta users, 87% Day-30 retention, and average 3.7 daily chat sessions per user."
  },
  {
    name: "Esmart Solution",
    year: "2020",
    role: "Founder", 
    impact: "Digital transformation consultancy for SMEs, serving 34 businesses with average 42% year-over-year online revenue growth."
  }
])

const accolades = ref([
  {
    year: "2024",
    title: "TEC National Startup Competition",
    achievement: "🏆 Grand Champion - Unanimous decision from all 14 judges"
  },
  {
    year: "2023", 
    title: "NestQuant Quantitative Finance Tournament",
    achievement: "🥇 Winner - Developed trading strategy with 3.1 Sharpe ratio"
  },
  {
    year: "2022",
    title: "Nielsen IQ Business Case Competition",
    achievement: "🥈 Runner-up - Designed DTC transformation strategy for CPG brands"
  },
  {
    year: "2022",
    title: "Battle of Minds Business Hackathon",
    achievement: "🥈 Runner-up - Innovative fintech solution development"
  },
  {
    year: "2021",
    title: "MacStartup Grant",
    achievement: "💡 $7,000 funding for student entrepreneurship initiatives"
  },
  {
    year: "2017",
    title: "World Mathematics Team Championship",
    achievement: "🥇 Gold Medal - International mathematics competition"
  }
])

const orbits = ref([
  {
    org: "Blackstone → Revantage",
    year: "2024", 
    contribution: "Valuated 15 CRE assets ($350M) · built Monte‑Carlo rent stress‑test · mitigated $1.5M downside",
    tech: "Python (pandas, NumPy), Argus, Power BI"
  },
  {
    org: "Deloitte SEA",
    year: "2023",
    contribution: "Led COSO/ Basel III gap‑analysis for 2 banks · cut op‑risk events 20%",
    tech: "SQL, Tableau, Oracle GRC"
  },
  {
    org: "Caprae Private Equity", 
    year: "2022",
    contribution: "Diligenced 7 climate‑tech targets (< Series B) · 2 term‑sheets issued",
    tech: "PitchBook, VCIO, DCF in Excel"
  },
  {
    org: "Daikin NA / DetectAuto / Newwave",
    year: "2021‑22",
    contribution: "Deployed computer‑vision POCs, set up CI/CD pipelines", 
    tech: "Python, TensorFlow, AWS Lambda"
  }
])

const trajectory = ref([
  {
    num: "1️⃣",
    title: "AI × Finance OS",
    description: "democratise robo‑advice for ASEAN Gen Z"
  },
  {
    num: "2️⃣", 
    title: "Emerging‑Market Launchpad",
    description: "bridge US capital → SEA founders"
  },
  {
    num: "3️⃣",
    title: "Knowledge Hyper‑Lanes",
    description: "tokenised mentor credits across borders"
  }
])

const businessMindset = ref([
  {
    id: 1,
    icon: "🎯",
    title: "Customer-Centric Innovation",
    description: "Every solution starts with understanding real customer pain points and market needs.",
    example: "Built FinBud AI after discovering 87% of Gen Z struggle with financial literacy and planning."
  },
  {
    id: 2,
    icon: "🔄",
    title: "Iterative Development",
    description: "Fast prototyping, rapid feedback loops, and continuous improvement drive sustainable growth.",
    example: "Pathwise achieved 71% success rate through constant curriculum refinement based on mentee feedback."
  },
  {
    id: 3,
    icon: "🌐",
    title: "Ecosystem Thinking",
    description: "Building interconnected platforms that create compound value for all stakeholders.",
    example: "CF Hub connects students, mentors, and employers in a mutually beneficial learning ecosystem."
  },
  {
    id: 4,
    icon: "📊",
    title: "Data-Driven Decisions",
    description: "Quantitative analysis and metrics guide strategic choices and resource allocation.",
    example: "Used Monte Carlo simulations to optimize $1B debt stack and reduce risk exposure at Smithfield."
  },
  {
    id: 5,
    icon: "🤝",
    title: "Partnership & Collaboration",
    description: "Sustainable success comes from building strong relationships and win-win partnerships.",
    example: "Esmart Solution's profit-sharing model with 34 SMEs created 42% average revenue growth."
  },
  {
    id: 6,
    icon: "🚀",
    title: "Scalable Infrastructure",
    description: "Design systems and processes that can grow exponentially without proportional complexity.",
    example: "FinBud's microservices architecture supports 12K users with minimal operational overhead."
  }
])

const blogPosts = ref([
  {
    id: 1,
    category: "Entrepreneurship",
    date: "Dec 15, 2024",
    title: "Building Ecosystems, Not Just Products",
    excerpt: "Why the future of entrepreneurship lies in creating interconnected platforms that empower communities rather than isolated solutions.",
    tags: ["Startup", "Ecosystem", "Strategy"],
    readTime: 8
  },
  {
    id: 2,
    category: "Technology",
    date: "Dec 10, 2024",
    title: "The Rise of AI-First Fintech",
    excerpt: "How artificial intelligence is revolutionizing personal finance and what it means for the next generation of financial services.",
    tags: ["AI", "Fintech", "Innovation"],
    readTime: 6
  },
  {
    id: 3,
    category: "Finance",
    date: "Dec 5, 2024",
    title: "Monte Carlo Methods in Modern Finance",
    excerpt: "Practical applications of probabilistic modeling in corporate finance, from risk assessment to capital allocation decisions.",
    tags: ["Finance", "Modeling", "Risk"],
    readTime: 10
  },
  {
    id: 4,
    category: "Mentorship",
    date: "Nov 28, 2024",
    title: "Scaling Mentorship Through Technology",
    excerpt: "Lessons learned from building Pathwise and how technology can democratize access to quality mentorship and career guidance.",
    tags: ["Mentorship", "EdTech", "Impact"],
    readTime: 7
  },
  {
    id: 5,
    category: "Strategy",
    date: "Nov 20, 2024",
    title: "The Three Pillars of Tech Entrepreneurship",
    excerpt: "Breaking down the essential skills every tech entrepreneur needs: technical depth, financial acumen, and market understanding.",
    tags: ["Strategy", "Skills", "Leadership"],
    readTime: 9
  },
  {
    id: 6,
    category: "Innovation",
    date: "Nov 15, 2024",
    title: "From Idea to IPO: A Systems Approach",
    excerpt: "How to think about startup growth as interconnected systems rather than linear progression through traditional stages.",
    tags: ["Growth", "Systems", "Startup"],
    readTime: 12
  }
])

onMounted(() => {
  setupAnimations()
  setupAdvancedAnimations()
})

const setupAdvancedAnimations = () => {
  // Particles animation
  if (particlesRef.value) {
    const particles = particlesRef.value.querySelectorAll('.particle')
    particles.forEach((particle: Element, index: number) => {
      gsap.set(particle, {
        x: Math.random() * window.innerWidth,
        y: Math.random() * window.innerHeight,
        scale: Math.random() * 0.5 + 0.5,
        opacity: Math.random() * 0.5 + 0.3
      })
      
      gsap.to(particle, {
        y: '-=20',
        duration: 2 + Math.random() * 2,
        repeat: -1,
        yoyo: true,
        ease: 'power2.inOut',
        delay: index * 0.1
      })
    })
  }

  // Enhanced hover effects
  document.querySelectorAll('.hover-lift').forEach(element => {
    element.addEventListener('mouseenter', () => {
      gsap.to(element, { y: -10, scale: 1.05, duration: 0.3, ease: 'power2.out' })
    })
    
    element.addEventListener('mouseleave', () => {
      gsap.to(element, { y: 0, scale: 1, duration: 0.3, ease: 'power2.out' })
    })
  })

  // Floating elements parallax
  gsap.utils.toArray('.floating-element').forEach((element: any) => {
    gsap.to(element, {
      y: -30,
      scrollTrigger: {
        trigger: element,
        start: 'top bottom',
        end: 'bottom top',
        scrub: 1
      }
    })
  })
}

const setupAnimations = () => {
  // Hero animation timeline
  const heroTl = gsap.timeline()
  
  if (statusRef.value) {
    heroTl.from(statusRef.value, {
      opacity: 0,
      y: 30,
      duration: 0.8,
      ease: "power3.out"
    })
  }
  
  if (heroTitleRef.value) {
    heroTl.from(heroTitleRef.value, {
      opacity: 0,
      y: 50,
      duration: 1,
      ease: "power3.out"
    }, "-=0.5")
  }
  

  
  if (heroNavRef.value) {
    heroTl.from(heroNavRef.value.children, {
      opacity: 0,
      y: 20,
      duration: 0.6,
      stagger: 0.1,
      ease: "power3.out"
    }, "-=0.2")
  }
  
  // NEXBOT animation
  if (nexbotRef.value) {
    heroTl.from(nexbotRef.value, {
      opacity: 0,
      scale: 0.8,
      y: 50,
      duration: 1.2,
      ease: "back.out(1.7)"
    }, "-=0.8")
  }

  // Section animations
  const sections = [
    { ref: originTitleRef, items: [originItem1, originItem2, originItem3, originItem4] },
    { ref: directivesTitleRef, selector: '.directives-grid' },
    { ref: constellationsTitleRef, selector: '.constellations-grid' },
    { ref: triangleTitleRef, selector: '.triangle-container' },
    { ref: mindsetTitleRef, selector: '.mindset-grid' },
    { ref: blogTitleRef, selector: '.blog-grid' },
    { ref: accoladesTitleRef, selector: '.accolades-timeline' },
    { ref: orbitsTitleRef, selector: '.orbits-grid' },
    { ref: trajectoryTitleRef, selector: '.trajectory-grid' },
    { ref: contactTitleRef, selector: '.contact-grid' }
  ]

  sections.forEach(section => {
    if (section.ref.value) {
      // Animate section title
      ScrollTrigger.create({
        trigger: section.ref.value,
        start: "top 80%",
        animation: gsap.from(section.ref.value, {
          opacity: 0,
          y: 30,
          duration: 0.8,
          ease: "power3.out"
        })
      })

      // Animate content
      if (section.items) {
        // For origin items
        section.items.forEach((item, index) => {
          if (item.value) {
            ScrollTrigger.create({
              trigger: item.value,
              start: "top 85%",
              animation: gsap.from(item.value, {
                opacity: 0,
                x: -30,
                duration: 0.6,
                delay: index * 0.1,
                ease: "power3.out"
              })
            })
          }
        })
      } else if (section.selector) {
        // For other sections
        const content = section.ref.value.parentElement?.querySelector(section.selector)
        if (content) {
          ScrollTrigger.create({
            trigger: content,
            start: "top 80%",
            animation: gsap.from(content.children, {
              opacity: 0,
              y: 20,
              duration: 0.6,
              stagger: 0.1,
              ease: "power3.out"
            })
          })
        }
      }
    }
  })

  // Quote animation
  if (quoteRef.value) {
    ScrollTrigger.create({
      trigger: quoteRef.value,
      start: "top 80%",
      animation: gsap.from(quoteRef.value, {
        opacity: 0,
        scale: 0.95,
        duration: 1,
        ease: "back.out(1.7)"
      })
    })
  }
}
</script>

<style scoped>
/* BASE STYLES */
.portfolio {
  background: #ffffff;
  color: #000000;
  min-height: 100vh;
  font-family: var(--font-family-primary);
  line-height: 1.6;
  position: relative;
  z-index: 10;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.section {
  padding: 8rem 0;
  position: relative;
  z-index: 50;
}

.section-header {
  text-align: center;
  margin-bottom: 6rem;
}

.section-title {
  font-size: clamp(2.5rem, 5vw, 4rem);
  font-weight: var(--font-weight-bold);
  margin-bottom: 1.5rem;
  letter-spacing: -0.02em;
  line-height: 1.1;
}

.section-subtitle {
  font-size: 1.25rem;
  color: #666666;
  font-style: italic;
  max-width: 600px;
  margin: 0 auto;
}

/* HERO SECTION */
.hero-section {
  padding: 12rem 0 8rem;
  text-align: center;
  background: linear-gradient(135deg, #fafafa 0%, #ffffff 100%);
  border-bottom: 1px solid #e5e5e5;
  position: relative;
  overflow: hidden;
  min-height: 100vh;
}

/* PROFESSIONAL BACKGROUND */
.background-pattern {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
  opacity: 0.05;
  pointer-events: none;
  background-image: 
    radial-gradient(circle at 25% 25%, #000000 1px, transparent 1px),
    radial-gradient(circle at 75% 75%, #000000 1px, transparent 1px);
  background-size: 50px 50px;
  background-position: 0 0, 25px 25px;
}

/* FLOATING ELEMENTS */
.floating-element {
  position: relative;
  z-index: 100;
}

.status-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.75rem 1.5rem;
  background: #f8f9fa;
  border: 1px solid #e9ecef;
  border-radius: 2rem;
  margin-bottom: 3rem;
  font-size: 0.875rem;
  font-weight: var(--font-weight-medium);
  color: #495057;
}

.status-dot {
  width: 8px;
  height: 8px;
  background: #28a745;
  border-radius: 50%;
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0% { box-shadow: 0 0 0 0 rgba(40, 167, 69, 0.4); }
  70% { box-shadow: 0 0 0 10px rgba(40, 167, 69, 0); }
  100% { box-shadow: 0 0 0 0 rgba(40, 167, 69, 0); }
}

/* ADVANCED ANIMATIONS */
.rotating {
  animation: rotate 10s linear infinite;
}

@keyframes rotate {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

.typewriter {
  overflow: hidden;
  border-right: 3px solid #000000;
  white-space: nowrap;
  animation: typewriter 4s steps(40, end), blink-caret 0.75s step-end infinite;
}

@keyframes typewriter {
  from { width: 0; }
  to { width: 100%; }
}

@keyframes blink-caret {
  from, to { border-color: transparent; }
  50% { border-color: #000000; }
}

.glitch-text {
  position: relative;
}

.glitch-text:before,
.glitch-text:after {
  content: attr(data-text);
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: transparent;
}

.pulse {
  animation: pulse-scale 2s ease-in-out infinite alternate;
}

@keyframes pulse-scale {
  0% { transform: scale(1); }
  100% { transform: scale(1.05); }
}

.fade-in {
  animation: fadeInUp 1s ease-out 1s both;
}

@keyframes fadeInUp {
  0% {
    opacity: 0;
    transform: translateY(30px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

.slide-up {
  animation: slideUp 1s ease-out 1.5s both;
}

@keyframes slideUp {
  0% {
    opacity: 0;
    transform: translateY(50px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

/* HOVER EFFECTS */
.hover-lift {
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  cursor: pointer;
}

.hover-lift:hover {
  transform: translateY(-5px) scale(1.02);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
}

/* COUNTER ANIMATIONS */
.counter-animation {
  font-variant-numeric: tabular-nums;
}

/* STAT GLOW EFFECTS */
.stat-glow {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 100%;
  height: 100%;
  background: radial-gradient(circle, rgba(0, 0, 0, 0.1) 0%, transparent 70%);
  border-radius: 50%;
  transform: translate(-50%, -50%) scale(0);
  transition: transform 0.3s ease;
  pointer-events: none;
}

.stat-item:hover .stat-glow {
  transform: translate(-50%, -50%) scale(1.2);
}

.hero-title {
  font-size: clamp(2.5rem, 6vw, 4.5rem);
  font-weight: var(--font-weight-bold);
  margin: 0 0 2rem;
  letter-spacing: -0.03em;
  line-height: 1.2;
  text-align: center;
}

.professional-title .title-main {
  display: block;
  font-weight: var(--font-weight-medium);
  color: #333333;
}

.professional-title .strong-emphasis {
  display: block;
  font-weight: var(--font-weight-bold);
  color: #000000;
  margin-top: 0.5rem;
}

.galaxy-icon {
  font-size: 0.8em;
}

.title-separator {
  color: #666666;
  font-weight: var(--font-weight-regular);
}

.title-sub {
  color: #333333;
}

.hero-subtitle {
  font-size: clamp(1.125rem, 2.5vw, 1.5rem);
  color: #666666;
  font-style: italic;
  margin-bottom: 4rem;
  max-width: 700px;
  margin-left: auto;
  margin-right: auto;
}

.hero-stats {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 3rem;
  max-width: 600px;
  margin: 0 auto 4rem;
  padding: 3rem 0;
  border-top: 1px solid #e9ecef;
  border-bottom: 1px solid #e9ecef;
}

.stat-item {
  text-align: center;
  position: relative;
  padding: 1.5rem;
  border-radius: 1rem;
  transition: all 0.3s ease;
}

.stat-number {
  font-size: 2.5rem;
  font-weight: var(--font-weight-bold);
  font-family: var(--font-family-mono);
  color: #000000;
  margin-bottom: 0.5rem;
}

.stat-label {
  font-size: 0.875rem;
  color: #666666;
  text-transform: uppercase;
  letter-spacing: 0.1em;
}

.hero-nav {
  display: flex;
  justify-content: center;
  gap: 2rem;
  flex-wrap: wrap;
  margin-top: 3rem;
}

.nav-link {
  color: #000000;
  text-decoration: none;
  font-weight: var(--font-weight-medium);
  padding: 1rem 2rem;
  border: 1px solid #dee2e6;
  border-radius: 0.5rem;
  transition: all 0.3s ease;
  font-size: 0.875rem;
  letter-spacing: 0.025em;
  background: #ffffff;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.nav-link:hover {
  background: #000000;
  color: #ffffff;
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

/* ORIGIN SECTION */
.origin-section {
  background: #fafafa;
}

.origin-grid {
  display: grid;
  gap: 2rem;
  max-width: 900px;
  margin: 0 auto;
}

.origin-item {
  display: grid;
  grid-template-columns: 200px 1fr;
  gap: 3rem;
  padding: 2.5rem;
  background: #ffffff;
  border: 1px solid #e9ecef;
  border-radius: 1rem;
  transition: all 0.3s ease;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.origin-item:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.origin-label {
  font-weight: var(--font-weight-bold);
  font-family: var(--font-family-mono);
  text-transform: uppercase;
  letter-spacing: 0.1em;
  font-size: 0.875rem;
  color: #495057;
}

.origin-value {
  font-size: 1.125rem;
  line-height: 1.7;
  color: #212529;
}

/* DIRECTIVES SECTION */
.directives-section {
  background: #ffffff;
}

.directives-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.directive-card {
  background: #fafafa;
  border: 1px solid #e9ecef;
  border-radius: 1rem;
  padding: 2.5rem;
  transition: all 0.3s ease;
  cursor: pointer;
  position: relative;
  overflow: hidden;
}

.directive-card:hover {
  transform: translateY(-8px) perspective(1000px) rotateX(15deg) rotateY(15deg) scale(1.08);
  box-shadow: 
    0 40px 80px rgba(100, 200, 255, 0.5),
    0 25px 50px rgba(0, 255, 136, 0.4),
    0 15px 30px rgba(0, 0, 0, 0.6),
    inset 0 0 0 1px rgba(100, 200, 255, 0.8);
  border-color: rgba(100, 200, 255, 0.9);
  background: rgba(0, 30, 60, 0.95);
  filter: brightness(1.2) contrast(1.1);
}

/* MORPHING CARDS */
.morphing-card {
  transform-style: preserve-3d;
  perspective: 1000px;
  position: relative;
  overflow: hidden;
}

.morphing-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.4), transparent);
  transition: left 0.5s;
  z-index: 1;
}

.morphing-card:hover::before {
  left: 100%;
}

.morphing-card:hover {
  transform: translateY(-16px) perspective(1000px) rotateX(20deg) rotateY(20deg) scale(1.1) translateZ(80px);
  box-shadow: 
    0 50px 100px rgba(100, 200, 255, 0.6),
    0 30px 60px rgba(0, 255, 136, 0.5),
    0 20px 40px rgba(0, 0, 0, 0.8),
    inset 0 0 0 2px rgba(100, 200, 255, 0.9),
    inset 0 2px 0 rgba(255, 255, 255, 0.3);
  background: rgba(0, 20, 40, 0.95);
  border-color: rgba(100, 200, 255, 1);
  filter: brightness(1.3) contrast(1.2) saturate(1.2);
}

/* FLOATING NUMBERS */
.floating-number {
  animation: float 3s ease-in-out infinite;
}

@keyframes float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-10px); }
}

/* ENHANCED CARD GLOW */
.card-glow {
  position: absolute;
  top: -3px;
  left: -3px;
  right: -3px;
  bottom: -3px;
  background: linear-gradient(45deg, 
    #000000, #333333, #666666, #999999, 
    #666666, #333333, #000000);
  border-radius: inherit;
  z-index: -1;
  opacity: 0;
  transition: all 0.5s ease;
  background-size: 600% 600%;
  animation: gradient-shift 6s ease infinite;
  filter: blur(8px);
}

@keyframes gradient-shift {
  0% { background-position: 0% 50%; transform: rotate(0deg); }
  25% { background-position: 100% 0%; transform: rotate(90deg); }
  50% { background-position: 100% 100%; transform: rotate(180deg); }
  75% { background-position: 0% 100%; transform: rotate(270deg); }
  100% { background-position: 0% 50%; transform: rotate(360deg); }
}

.directive-card:hover .card-glow {
  opacity: 0.8;
  filter: blur(12px);
  animation-duration: 3s;
}

/* ENHANCED CARD PARTICLES */
.card-particles {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  overflow: hidden;
  border-radius: inherit;
}

.card-particle {
  position: absolute;
  width: 3px;
  height: 3px;
  background: radial-gradient(circle, #666666, transparent);
  border-radius: 50%;
  opacity: 0;
  transition: all 0.5s ease;
}

.card-particle:nth-child(1) { 
  top: 15%; left: 15%; animation-delay: 0s; 
  background: radial-gradient(circle, #00ff88, transparent);
}
.card-particle:nth-child(2) { 
  top: 85%; left: 85%; animation-delay: 0.3s; 
  background: radial-gradient(circle, #ff4444, transparent);
}
.card-particle:nth-child(3) { 
  top: 50%; left: 25%; animation-delay: 0.6s; 
  background: radial-gradient(circle, #4488ff, transparent);
}
.card-particle:nth-child(4) { 
  top: 25%; left: 75%; animation-delay: 0.9s; 
  background: radial-gradient(circle, #ff8844, transparent);
}
.card-particle:nth-child(5) { 
  top: 75%; left: 50%; animation-delay: 1.2s; 
  background: radial-gradient(circle, #8844ff, transparent);
}

.directive-card:hover .card-particle {
  opacity: 1;
  animation: enhanced-particle-dance 3s ease-in-out infinite;
}

@keyframes enhanced-particle-dance {
  0%, 100% { 
    transform: translateY(0px) translateX(0px) scale(1) rotate(0deg); 
    opacity: 1;
  }
  25% { 
    transform: translateY(-20px) translateX(10px) scale(1.5) rotate(90deg); 
    opacity: 0.8;
  }
  50% { 
    transform: translateY(-10px) translateX(-15px) scale(1.2) rotate(180deg); 
    opacity: 0.6;
  }
  75% { 
    transform: translateY(-25px) translateX(20px) scale(1.8) rotate(270deg); 
    opacity: 0.9;
  }
}

/* SHIMMER EFFECTS */
.shimmer-effect {
  position: relative;
  overflow: hidden;
}

.shimmer-effect::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.4), transparent);
  transition: left 0.5s;
}

.shimmer-effect:hover::before {
  left: 100%;
}

/* GLOW EFFECTS */
.glow-on-hover {
  position: relative;
  transition: all 0.3s ease;
}

.glow-on-hover:hover {
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
  transform: translateY(-2px);
}

/* RIPPLE EFFECT */
.ripple-effect {
  position: relative;
  overflow: hidden;
}

.ripple-effect::after {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 0;
  height: 0;
  border-radius: 50%;
  background: rgba(0, 0, 0, 0.1);
  transform: translate(-50%, -50%);
  transition: width 0.6s, height 0.6s;
}

.ripple-effect:hover::after {
  width: 300px;
  height: 300px;
}

/* BREATHING ANIMATION */
.breathing-animation {
  animation: breathe 3s ease-in-out infinite;
}

@keyframes breathe {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.02); }
}

/* MAGNETIC FIELD EFFECT */
.magnetic-field {
  position: relative;
}

.magnetic-field::before {
  content: '';
  position: absolute;
  top: -5px;
  left: -5px;
  right: -5px;
  bottom: -5px;
  background: linear-gradient(45deg, transparent, rgba(0, 0, 0, 0.05), transparent);
  border-radius: inherit;
  opacity: 0;
  transition: opacity 0.3s ease;
  z-index: -1;
}

.magnetic-field:hover::before {
  opacity: 1;
  animation: rotate 2s linear infinite;
}

/* HOLOGRAPHIC EFFECT */
.holographic {
  position: relative;
  background: linear-gradient(45deg, #ffffff 25%, transparent 25%, transparent 75%, #ffffff 75%);
  background-size: 4px 4px;
  background-position: 0 0, 2px 2px;
  animation: hologram 2s linear infinite;
}

@keyframes hologram {
  0% { background-position: 0 0, 2px 2px; }
  100% { background-position: 4px 4px, 6px 6px; }
}

.directive-number {
  font-size: 3rem;
  font-weight: var(--font-weight-bold);
  font-family: var(--font-family-mono);
  color: #e9ecef;
  position: absolute;
  top: 1rem;
  right: 1.5rem;
  line-height: 1;
}

.directive-content {
  position: relative;
  z-index: 2;
}

.directive-title {
  font-size: 1.25rem;
  font-weight: var(--font-weight-bold);
  margin-bottom: 1rem;
  color: #212529;
}

.directive-description {
  color: #495057;
  line-height: 1.6;
}

/* CONSTELLATIONS SECTION */
.constellations-section {
  background: #fafafa;
}

.constellations-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
}

.constellation-card {
  background: #ffffff;
  border: 1px solid #e9ecef;
  border-radius: 1rem;
  padding: 2.5rem;
  transition: all 0.3s ease;
  cursor: pointer;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.constellation-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
  border-color: #000000;
}

/* STELLAR CARD EFFECTS */
.stellar-card {
  position: relative;
  overflow: hidden;
}

.glowing-text {
  position: relative;
  transition: all 0.3s ease;
}

.stellar-card:hover .glowing-text {
  text-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
}

.pulse-badge {
  position: relative;
  overflow: hidden;
}

.pulse-badge::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.4), transparent);
  transition: left 0.5s;
}

.stellar-card:hover .pulse-badge::before {
  left: 100%;
}

.animated-metric {
  position: relative;
  transition: all 0.3s ease;
}

.stellar-card:hover .animated-metric {
  transform: scale(1.02);
}

/* STELLAR GLOW */
.stellar-glow {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 0;
  height: 0;
  background: radial-gradient(circle, rgba(0, 0, 0, 0.1) 0%, transparent 70%);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  transition: all 0.5s ease;
  z-index: -1;
}

.stellar-card:hover .stellar-glow {
  width: 120%;
  height: 120%;
}

/* CONSTELLATION LINES */
.constellation-lines {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  overflow: hidden;
}

.constellation-lines .line {
  position: absolute;
  background: #000000;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.constellation-lines .line:nth-child(1) {
  top: 20%;
  left: 10%;
  width: 30px;
  height: 1px;
  transform: rotate(45deg);
}

.constellation-lines .line:nth-child(2) {
  top: 60%;
  right: 10%;
  width: 25px;
  height: 1px;
  transform: rotate(-30deg);
}

.constellation-lines .line:nth-child(3) {
  bottom: 20%;
  left: 30%;
  width: 20px;
  height: 1px;
  transform: rotate(15deg);
}

.stellar-card:hover .constellation-lines .line {
  opacity: 0.3;
  animation: line-draw 1s ease-out;
}

@keyframes line-draw {
  0% {
    width: 0;
  }
  100% {
    width: 30px;
  }
}

.card-header {
  margin-bottom: 1.5rem;
}

.venture-name {
  font-size: 1.5rem;
  font-weight: var(--font-weight-bold);
  margin-bottom: 0.75rem;
  color: #212529;
}

.venture-meta {
  display: flex;
  gap: 1rem;
  align-items: center;
}

.venture-year {
  background: #000000;
  color: #ffffff;
  padding: 0.25rem 0.75rem;
  border-radius: 0.5rem;
  font-size: 0.75rem;
  font-weight: var(--font-weight-bold);
  font-family: var(--font-family-mono);
}

.venture-role {
  color: #666666;
  font-size: 0.875rem;
  font-weight: var(--font-weight-medium);
}

.impact-metric {
  background: #f8f9fa;
  padding: 1.5rem;
  border-radius: 0.75rem;
  font-size: 0.95rem;
  line-height: 1.6;
  color: #495057;
  border-left: 4px solid #000000;
}

/* ACCOLADES SECTION */
.accolades-section {
  background: #ffffff;
}

.accolades-timeline {
  max-width: 800px;
  margin: 0 auto;
  position: relative;
}

.accolades-timeline::before {
  content: '';
  position: absolute;
  left: 60px;
  top: 0;
  bottom: 0;
  width: 2px;
  background: #e9ecef;
}

.timeline-item {
  display: grid;
  grid-template-columns: 120px 1fr;
  gap: 3rem;
  margin-bottom: 3rem;
  position: relative;
  cursor: pointer;
  transition: all 0.3s ease;
}

.timeline-item:hover {
  transform: translateX(10px);
}

.timeline-year {
  font-size: 1.5rem;
  font-weight: var(--font-weight-bold);
  font-family: var(--font-family-mono);
  color: #000000;
  text-align: center;
  position: relative;
}

.timeline-year::after {
  content: '';
  position: absolute;
  right: -1.75rem;
  top: 50%;
  transform: translateY(-50%);
  width: 12px;
  height: 12px;
  background: #000000;
  border-radius: 50%;
  border: 3px solid #ffffff;
  box-shadow: 0 0 0 2px #e9ecef;
}

.timeline-content {
  background: #fafafa;
  padding: 2rem;
  border-radius: 1rem;
  border: 1px solid #e9ecef;
  transition: all 0.3s ease;
}

.timeline-item:hover .timeline-content {
  border-color: #000000;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.accolade-title {
  font-size: 1.25rem;
  font-weight: var(--font-weight-bold);
  margin-bottom: 0.75rem;
  color: #212529;
}

.accolade-achievement {
  font-size: 1.125rem;
  color: #495057;
}

/* ORBITS SECTION */
.orbits-section {
  background: #fafafa;
}

.orbits-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
}

.orbit-card {
  background: #ffffff;
  border: 1px solid #e9ecef;
  border-radius: 1rem;
  padding: 2.5rem;
  transition: all 0.3s ease;
  cursor: pointer;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.orbit-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
  border-color: #000000;
}

.orbit-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1.5rem;
}

.orbit-org {
  font-size: 1.25rem;
  font-weight: var(--font-weight-bold);
  color: #212529;
}

.orbit-year {
  background: #f8f9fa;
  padding: 0.25rem 0.75rem;
  border-radius: 0.5rem;
  font-size: 0.75rem;
  font-weight: var(--font-weight-bold);
  font-family: var(--font-family-mono);
  color: #495057;
}

.orbit-contribution {
  margin-bottom: 1.5rem;
  line-height: 1.6;
  color: #495057;
}

.orbit-tech {
  background: #f8f9fa;
  padding: 1rem;
  border-radius: 0.5rem;
  border-left: 3px solid #000000;
}

.tech-label {
  font-weight: var(--font-weight-semibold);
  color: #212529;
  margin-right: 0.5rem;
}

.tech-list {
  color: #495057;
  font-family: var(--font-family-mono);
  font-size: 0.875rem;
}

/* TRAJECTORY SECTION */
.trajectory-section {
  background: #ffffff;
}

.trajectory-grid {
  display: grid;
  gap: 2rem;
  max-width: 800px;
  margin: 0 auto;
}

.trajectory-card {
  display: grid;
  grid-template-columns: 80px 1fr;
  gap: 2rem;
  align-items: center;
  background: #fafafa;
  padding: 2.5rem;
  border-radius: 1rem;
  border: 1px solid #e9ecef;
  transition: all 0.3s ease;
  cursor: pointer;
}

.trajectory-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  border-color: #000000;
}

.trajectory-number {
  font-size: 2.5rem;
  text-align: center;
}

.trajectory-title {
  font-size: 1.5rem;
  font-weight: var(--font-weight-bold);
  margin-bottom: 0.5rem;
  color: #212529;
}

.trajectory-description {
  color: #666666;
  font-style: italic;
  line-height: 1.6;
}

/* CONTACT SECTION */
.contact-section {
  background: #fafafa;
  text-align: center;
}

.contact-cta {
  max-width: 700px;
  margin: 4rem auto;
}

.contact-description {
  font-size: 1.25rem;
  color: #666666;
  line-height: 1.6;
  margin-bottom: 3rem;
  font-style: italic;
}

.contact-buttons {
  display: flex;
  gap: 1.5rem;
  justify-content: center;
  flex-wrap: wrap;
}

.contact-btn {
  display: inline-flex;
  align-items: center;
  gap: 0.75rem;
  padding: 1rem 2rem;
  border-radius: 0.75rem;
  text-decoration: none;
  font-weight: var(--font-weight-semibold);
  font-size: 1rem;
  transition: all 0.3s ease;
  border: 2px solid transparent;
  position: relative;
  overflow: hidden;
}

.contact-btn svg {
  width: 20px;
  height: 20px;
}

.contact-btn.primary {
  background: #000000;
  color: #ffffff;
  border-color: #000000;
}

.contact-btn.primary:hover {
  background: #333333;
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.2);
}

.contact-btn.secondary {
  background: #ffffff;
  color: #000000;
  border-color: #e9ecef;
}

.contact-btn.secondary:hover {
  background: #000000;
  color: #ffffff;
  border-color: #000000;
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.1);
}

.quote-section {
  margin-top: 6rem;
  padding: 4rem 0;
  border-top: 1px solid #e9ecef;
}

.elegant-quote {
  font-size: clamp(1.5rem, 3vw, 2.5rem);
  font-style: italic;
  font-weight: var(--font-weight-medium);
  color: #212529;
  max-width: 600px;
  margin: 0 auto;
  line-height: 1.4;
  quotes: """ """ "'" "'";
}

.elegant-quote:before {
  content: open-quote;
  color: #dee2e6;
  font-size: 1.5em;
  margin-right: 0.1em;
}

.elegant-quote:after {
  content: close-quote;
  color: #dee2e6;
  font-size: 1.5em;
  margin-left: 0.1em;
}

/* ELEGANT LINKS */
.elegant-link {
  display: inline-flex;
  align-items: center;
  gap: 0.75rem;
  color: #000000;
  text-decoration: none;
  font-weight: var(--font-weight-medium);
  padding: 1rem 2rem;
  border: 1px solid #dee2e6;
  border-radius: 0.75rem;
  transition: all 0.3s ease;
  background: #ffffff;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.elegant-link:hover {
  background: #000000;
  color: #ffffff;
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

.link-arrow {
  transition: transform 0.3s ease;
}

.elegant-link:hover .link-arrow {
  transform: translateX(4px);
}

.trophy-link,
.roadmap-link {
  text-align: center;
  margin-top: 3rem;
}

/* FOOTER SECTION */
.footer-section {
  background: #000000;
  color: #ffffff;
  padding: 4rem 0 2rem;
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
}

.footer-grid {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr;
  gap: 4rem;
  margin-bottom: 3rem;
}

.footer-brand {
  max-width: 400px;
}

.footer-logo {
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 1rem;
  color: #ffffff;
}

.footer-description {
  color: #cccccc;
  line-height: 1.6;
  margin-bottom: 2rem;
}

.footer-social {
  display: flex;
  gap: 1rem;
}

.social-link {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 50%;
  color: #cccccc;
  text-decoration: none;
  transition: all 0.3s ease;
}

.social-link:hover {
  background: #ffffff;
  color: #000000;
  transform: translateY(-2px);
}

.social-link svg {
  width: 20px;
  height: 20px;
}

.footer-heading {
  font-size: 1.125rem;
  font-weight: 600;
  margin-bottom: 1.5rem;
  color: #ffffff;
}

.footer-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer-list li {
  margin-bottom: 0.75rem;
}

.footer-link {
  color: #cccccc;
  text-decoration: none;
  transition: color 0.3s ease;
}

.footer-link:hover {
  color: #ffffff;
}

.contact-item {
  margin-bottom: 1rem;
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
}

.contact-label {
  font-size: 0.875rem;
  color: #999999;
  text-transform: uppercase;
  letter-spacing: 0.1em;
}

.contact-link {
  color: #cccccc;
  text-decoration: none;
  transition: color 0.3s ease;
}

.contact-link:hover {
  color: #ffffff;
}

.contact-text {
  color: #cccccc;
}

.footer-bottom {
  margin-top: 3rem;
}

.footer-divider {
  height: 1px;
  background: rgba(255, 255, 255, 0.1);
  margin-bottom: 2rem;
}

.footer-bottom-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
}

.footer-copyright {
  color: #999999;
  font-size: 0.875rem;
  margin: 0;
}

.footer-quote {
  color: #cccccc;
  font-style: italic;
  margin: 0;
}

/* NEXBOT SECTION */
.nexbot-section {
  margin: 6rem 0;
  max-width: 800px;
  margin-left: auto;
  margin-right: auto;
  position: relative;
  z-index: 5;
}

.nexbot-section::before {
  content: '';
  position: absolute;
  top: -20px;
  left: -20px;
  right: -20px;
  bottom: -20px;
  background: linear-gradient(45deg, transparent, rgba(0, 255, 136, 0.1), transparent);
  border-radius: 30px;
  z-index: -1;
  opacity: 0;
  transition: opacity 0.5s ease;
}

.nexbot-section:hover::before {
  opacity: 1;
  animation: nexbot-aura 3s ease-in-out infinite;
}

@keyframes nexbot-aura {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.05); }
}

/* RESPONSIVE */
@media (max-width: 768px) {
  .section {
    padding: 4rem 0;
  }
  
  .hero-section {
    padding: 6rem 0 4rem;
  }
  
  .hero-title {
    flex-direction: column;
    gap: 0.5rem;
  }
  
  .hero-stats {
    grid-template-columns: 1fr;
    gap: 2rem;
    max-width: 300px;
  }
  
  .hero-nav {
    gap: 1rem;
  }
  
  .nav-link {
    padding: 0.75rem 1.5rem;
    font-size: 0.75rem;
  }
  
  .origin-item,
  .timeline-item {
    grid-template-columns: 1fr;
    gap: 1rem;
  }
  
  .timeline-year::after {
    display: none;
  }
  
  .accolades-timeline::before {
    display: none;
  }
  
  .directives-grid,
  .constellations-grid,
  .orbits-grid {
    grid-template-columns: 1fr;
  }
  
  .trajectory-card {
    grid-template-columns: 1fr;
    text-align: center;
  }
  
  .contact-buttons {
    flex-direction: column;
    align-items: center;
  }
  
  .contact-btn {
    width: 100%;
    max-width: 280px;
    justify-content: center;
  }

  .footer-grid {
    grid-template-columns: 1fr;
    gap: 2rem;
    text-align: center;
  }

  .footer-bottom-content {
    flex-direction: column;
    text-align: center;
  }
}

@media (max-width: 480px) {
  .container {
    padding: 0 1rem;
  }
  
  .section-header {
    margin-bottom: 4rem;
  }
  
  .origin-item,
  .directive-card,
  .constellation-card,
  .orbit-card,
  .trajectory-card {
    padding: 1.5rem;
  }
}

/* ===== MYSTICAL OVERLAY EFFECTS ===== */
.mystical-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 3;
  pointer-events: none;
  overflow: hidden;
}

/* Magical Floating Shapes */
.magical-shapes-layer {
  position: absolute;
  width: 100%;
  height: 100%;
}

.magical-shape {
  position: absolute;
  opacity: 0;
  animation: magical-float 8s ease-in-out infinite;
}

.diamond-shape {
  width: 20px;
  height: 20px;
  background: linear-gradient(45deg, #ffffff, #cccccc);
  transform: rotate(45deg);
  box-shadow: 0 0 15px rgba(255, 255, 255, 0.6);
  animation-duration: 10s;
}

.triangle-shape {
  width: 0;
  height: 0;
  border-left: 12px solid transparent;
  border-right: 12px solid transparent;
  border-bottom: 20px solid #666666;
  box-shadow: 0 0 12px rgba(102, 102, 102, 0.5);
  animation-duration: 12s;
}

.hexagon-shape {
  width: 24px;
  height: 24px;
  background: #888888;
  clip-path: polygon(25% 0%, 75% 0%, 100% 50%, 75% 100%, 25% 100%, 0% 50%);
  box-shadow: 0 0 18px rgba(136, 136, 136, 0.7);
  animation-duration: 14s;
}

.star-shape {
  width: 18px;
  height: 18px;
  background: #aaaaaa;
  clip-path: polygon(50% 0%, 61% 35%, 98% 35%, 68% 57%, 79% 91%, 50% 70%, 21% 91%, 32% 57%, 2% 35%, 39% 35%);
  box-shadow: 0 0 20px rgba(170, 170, 170, 0.8);
  animation-duration: 16s;
}

/* Dynamic positioning for shapes */
.diamond-shape:nth-child(1) { left: 15%; top: 20%; animation-delay: 0s; }
.diamond-shape:nth-child(2) { left: 75%; top: 35%; animation-delay: 2s; }
.diamond-shape:nth-child(3) { left: 45%; top: 70%; animation-delay: 4s; }
.diamond-shape:nth-child(4) { left: 85%; top: 15%; animation-delay: 6s; }
.diamond-shape:nth-child(5) { left: 25%; top: 60%; animation-delay: 1s; }
.diamond-shape:nth-child(6) { left: 65%; top: 80%; animation-delay: 3s; }
.diamond-shape:nth-child(7) { left: 35%; top: 25%; animation-delay: 5s; }
.diamond-shape:nth-child(8) { left: 55%; top: 45%; animation-delay: 7s; }

.triangle-shape:nth-child(1) { left: 20%; top: 30%; animation-delay: 1s; }
.triangle-shape:nth-child(2) { left: 70%; top: 55%; animation-delay: 3s; }
.triangle-shape:nth-child(3) { left: 40%; top: 15%; animation-delay: 5s; }
.triangle-shape:nth-child(4) { left: 80%; top: 75%; animation-delay: 2s; }
.triangle-shape:nth-child(5) { left: 30%; top: 85%; animation-delay: 4s; }
.triangle-shape:nth-child(6) { left: 60%; top: 10%; animation-delay: 6s; }

.hexagon-shape:nth-child(1) { left: 25%; top: 40%; animation-delay: 2s; }
.hexagon-shape:nth-child(2) { left: 65%; top: 65%; animation-delay: 4s; }
.hexagon-shape:nth-child(3) { left: 85%; top: 25%; animation-delay: 6s; }
.hexagon-shape:nth-child(4) { left: 45%; top: 85%; animation-delay: 1s; }
.hexagon-shape:nth-child(5) { left: 15%; top: 65%; animation-delay: 3s; }

.star-shape:nth-child(1) { left: 35%; top: 50%; animation-delay: 3s; }
.star-shape:nth-child(2) { left: 75%; top: 20%; animation-delay: 5s; }
.star-shape:nth-child(3) { left: 55%; top: 75%; animation-delay: 1s; }
.star-shape:nth-child(4) { left: 95%; top: 45%; animation-delay: 7s; }
.star-shape:nth-child(5) { left: 25%; top: 75%; animation-delay: 2s; }
.star-shape:nth-child(6) { left: 65%; top: 35%; animation-delay: 4s; }
.star-shape:nth-child(7) { left: 45%; top: 5%; animation-delay: 6s; }

@keyframes magical-float {
  0%, 100% { 
    opacity: 0; 
    transform: translateY(0) translateX(0) scale(1) rotate(0deg); 
  }
  15% { 
    opacity: 0.8; 
    transform: translateY(-30px) translateX(20px) scale(1.2) rotate(45deg); 
  }
  30% { 
    opacity: 1; 
    transform: translateY(-60px) translateX(-15px) scale(1.5) rotate(90deg); 
  }
  45% { 
    opacity: 0.7; 
    transform: translateY(-45px) translateX(35px) scale(1.3) rotate(135deg); 
  }
  60% { 
    opacity: 1; 
    transform: translateY(-80px) translateX(-25px) scale(1.8) rotate(180deg); 
  }
  75% { 
    opacity: 0.6; 
    transform: translateY(-55px) translateX(40px) scale(1.4) rotate(225deg); 
  }
  90% { 
    opacity: 0.9; 
    transform: translateY(-90px) translateX(-10px) scale(2) rotate(270deg); 
  }
}

/* Particle Trails */
.particle-trails-layer {
  position: absolute;
  width: 100%;
  height: 100%;
}

.particle-trail {
  position: absolute;
  animation: trail-movement 6s linear infinite;
}

.particle-trail:nth-child(1) { left: 10%; top: 25%; animation-delay: 0s; }
.particle-trail:nth-child(2) { left: 70%; top: 45%; animation-delay: 0.5s; }
.particle-trail:nth-child(3) { left: 30%; top: 65%; animation-delay: 1s; }
.particle-trail:nth-child(4) { left: 90%; top: 15%; animation-delay: 1.5s; }
.particle-trail:nth-child(5) { left: 50%; top: 85%; animation-delay: 2s; }
.particle-trail:nth-child(6) { left: 80%; top: 55%; animation-delay: 2.5s; }
.particle-trail:nth-child(7) { left: 20%; top: 75%; animation-delay: 3s; }
.particle-trail:nth-child(8) { left: 60%; top: 35%; animation-delay: 3.5s; }
.particle-trail:nth-child(9) { left: 40%; top: 5%; animation-delay: 4s; }
.particle-trail:nth-child(10) { left: 95%; top: 85%; animation-delay: 4.5s; }
.particle-trail:nth-child(11) { left: 15%; top: 55%; animation-delay: 5s; }
.particle-trail:nth-child(12) { left: 75%; top: 95%; animation-delay: 5.5s; }

.trail-dot {
  position: absolute;
  width: 3px;
  height: 3px;
  background: radial-gradient(circle, #777777, transparent);
  border-radius: 50%;
  opacity: 0;
  animation: dot-trail 2s ease-in-out infinite;
}

.trail-dot:nth-child(1) { left: 0; animation-delay: 0s; }
.trail-dot:nth-child(2) { left: 15px; animation-delay: 0.25s; }
.trail-dot:nth-child(3) { left: 30px; animation-delay: 0.5s; }
.trail-dot:nth-child(4) { left: 45px; animation-delay: 0.75s; }
.trail-dot:nth-child(5) { left: 60px; animation-delay: 1s; }
.trail-dot:nth-child(6) { left: 75px; animation-delay: 1.25s; }
.trail-dot:nth-child(7) { left: 90px; animation-delay: 1.5s; }
.trail-dot:nth-child(8) { left: 105px; animation-delay: 1.75s; }

@keyframes trail-movement {
  0% { transform: translateY(100vh) translateX(-50px); opacity: 0; }
  10% { opacity: 1; }
  90% { opacity: 1; }
  100% { transform: translateY(-100px) translateX(50px); opacity: 0; }
}

@keyframes dot-trail {
  0%, 100% { 
    opacity: 0; 
    transform: translateY(0) scale(1); 
    box-shadow: 0 0 5px #777777;
  }
  50% { 
    opacity: 1; 
    transform: translateY(-20px) scale(1.5); 
    box-shadow: 0 0 15px #777777;
  }
}

/* Energy Waves */
.energy-waves-layer {
  position: absolute;
  width: 100%;
  height: 100%;
}

.energy-wave {
  position: absolute;
  width: 200px;
  height: 40px;
  background: linear-gradient(90deg, 
    transparent 0%, 
    rgba(255, 255, 255, 0.1) 25%, 
    rgba(255, 255, 255, 0.3) 50%, 
    rgba(255, 255, 255, 0.1) 75%, 
    transparent 100%);
  border-radius: 20px;
  opacity: 0;
  animation: energy-pulse 4s ease-in-out infinite;
  filter: blur(2px);
}

.energy-wave:nth-child(1) { 
  left: 20%; top: 30%; 
  animation-delay: 0s; 
  background: linear-gradient(90deg, transparent, rgba(0, 255, 136, 0.3), transparent);
}
.energy-wave:nth-child(2) { 
  left: 60%; top: 50%; 
  animation-delay: 1s; 
  background: linear-gradient(90deg, transparent, rgba(255, 68, 68, 0.3), transparent);
}
.energy-wave:nth-child(3) { 
  left: 40%; top: 70%; 
  animation-delay: 2s; 
  background: linear-gradient(90deg, transparent, rgba(68, 136, 255, 0.3), transparent);
}
.energy-wave:nth-child(4) { 
  left: 80%; top: 20%; 
  animation-delay: 3s; 
  background: linear-gradient(90deg, transparent, rgba(136, 68, 255, 0.3), transparent);
}
.energy-wave:nth-child(5) { 
  left: 10%; top: 60%; 
  animation-delay: 0.5s; 
  background: linear-gradient(90deg, transparent, rgba(255, 170, 68, 0.3), transparent);
}
.energy-wave:nth-child(6) { 
  left: 70%; top: 80%; 
  animation-delay: 1.5s; 
  background: linear-gradient(90deg, transparent, rgba(170, 255, 68, 0.3), transparent);
}

@keyframes energy-pulse {
  0%, 100% { 
    opacity: 0; 
    transform: scaleX(0.5) scaleY(1) translateY(0); 
  }
  25% { 
    opacity: 0.7; 
    transform: scaleX(1.2) scaleY(1.5) translateY(-10px); 
  }
  50% { 
    opacity: 1; 
    transform: scaleX(2) scaleY(2) translateY(-20px); 
  }
  75% { 
    opacity: 0.8; 
    transform: scaleX(1.5) scaleY(1.8) translateY(-15px); 
  }
}

/* Responsive Mystical Adjustments */
@media (max-width: 768px) {
  .magical-shape {
    width: 15px !important;
    height: 15px !important;
  }
  
  .diamond-shape { width: 12px; height: 12px; }
  .triangle-shape { 
    border-left: 8px solid transparent;
    border-right: 8px solid transparent;
    border-bottom: 14px solid #ff4444;
  }
  .hexagon-shape { width: 16px; height: 16px; }
  .star-shape { width: 12px; height: 12px; }
  
  .trail-dot { width: 2px; height: 2px; }
  .energy-wave { width: 120px; height: 25px; }
}

/* ===== COSMIC TEXT EFFECTS ===== */
.cosmic-text {
  position: relative;
}

.glitch-text {
  position: relative;
  display: inline-block;
}

.glitch-text::before,
.glitch-text::after {
  content: attr(data-text);
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: transparent;
  overflow: hidden;
  opacity: 0;
}

.glitch-text::before {
  color: #ffffff;
  z-index: -1;
  animation: glitch-1 2s infinite;
}

.glitch-text::after {
  color: #666666;
  z-index: -2;
  animation: glitch-2 2s infinite;
}

@keyframes glitch-1 {
  0%, 90%, 100% { opacity: 0; }
  5% { opacity: 1; transform: translate(-2px, -2px); }
  10% { opacity: 0; }
  15% { opacity: 1; transform: translate(2px, 2px); }
  20% { opacity: 0; }
}

@keyframes glitch-2 {
  0%, 90%, 100% { opacity: 0; }
  10% { opacity: 1; transform: translate(2px, -2px); }
  15% { opacity: 0; }
  20% { opacity: 1; transform: translate(-2px, 2px); }
  25% { opacity: 0; }
}

.typewriter-text {
  overflow: hidden;
  border-right: 3px solid #000000;
  white-space: nowrap;
  animation: typewriter 4s steps(40, end) 2s 1 normal both,
             blink-caret 0.75s step-end infinite 2s;
}

@keyframes typewriter {
  from { width: 0; }
  to { width: 100%; }
}

@keyframes blink-caret {
  from, to { border-color: transparent; }
  50% { border-color: #000000; }
}

/* ===== SECTION PLANETS ===== */
.section-planets {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  overflow: hidden;
  z-index: 1;
}

.planet {
  position: absolute;
  border-radius: 50%;
  background: radial-gradient(circle at 30% 30%, #ffffff, #666666, #333333);
}

.planet-1 {
  width: 80px;
  height: 80px;
  top: 15%;
  right: 10%;
  animation: planet-float 20s linear infinite;
}

.planet-2 {
  width: 60px;
  height: 60px;
  bottom: 20%;
  left: 8%;
  animation: planet-drift 25s linear infinite reverse;
}

.planet-3 {
  width: 100px;
  height: 100px;
  top: 30%;
  right: 15%;
  animation: planet-rotate 30s linear infinite;
}

.planet-ring {
  position: absolute;
  top: -15px;
  left: -15px;
  right: -15px;
  bottom: -15px;
  border: 2px solid rgba(255, 255, 255, 0.3);
  border-radius: 50%;
  animation: ring-rotate 15s linear infinite;
}

.planet-moon {
  position: absolute;
  width: 15px;
  height: 15px;
  background: #cccccc;
  border-radius: 50%;
  top: -30px;
  left: 50%;
  margin-left: -7.5px;
  animation: moon-orbit 8s linear infinite;
}

.planet-atmosphere {
  position: absolute;
  top: -10px;
  left: -10px;
  right: -10px;
  bottom: -10px;
  background: radial-gradient(circle, transparent 60%, rgba(255, 255, 255, 0.1) 80%, transparent 100%);
  border-radius: 50%;
  animation: atmosphere-pulse 4s ease-in-out infinite;
}

.planet-glow {
  position: absolute;
  top: -20px;
  left: -20px;
  right: -20px;
  bottom: -20px;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.1) 0%, transparent 70%);
  border-radius: 50%;
  animation: glow-pulse 3s ease-in-out infinite;
}

@keyframes planet-float {
  0%, 100% { transform: translateY(0) rotate(0deg); }
  25% { transform: translateY(-20px) rotate(90deg); }
  50% { transform: translateY(-10px) rotate(180deg); }
  75% { transform: translateY(-30px) rotate(270deg); }
}

@keyframes planet-drift {
  0% { transform: translateX(0) rotate(0deg); }
  100% { transform: translateX(50px) rotate(360deg); }
}

@keyframes planet-rotate {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

@keyframes ring-rotate {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

@keyframes moon-orbit {
  0% { transform: rotate(0deg) translateY(-40px) rotate(0deg); }
  100% { transform: rotate(360deg) translateY(-40px) rotate(-360deg); }
}

@keyframes atmosphere-pulse {
  0%, 100% { opacity: 0.3; transform: scale(1); }
  50% { opacity: 0.6; transform: scale(1.1); }
}

@keyframes glow-pulse {
  0%, 100% { opacity: 0.5; transform: scale(1); }
  50% { opacity: 1; transform: scale(1.2); }
}

/* Orbital Paths */
.orbital-path {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 200px;
  height: 200px;
  margin: -100px 0 0 -100px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 50%;
  animation: orbital-path-rotate 40s linear infinite;
}

.orbiting-object {
  position: absolute;
  width: 8px;
  height: 8px;
  background: #ffffff;
  border-radius: 50%;
  top: 0;
  left: 50%;
  margin-left: -4px;
  animation: object-orbit 10s linear infinite;
}

@keyframes orbital-path-rotate {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

@keyframes object-orbit {
  0% { transform: rotate(0deg) translateY(-100px) rotate(0deg); }
  100% { transform: rotate(360deg) translateY(-100px) rotate(-360deg); }
}

/* Section Cosmos */
.section-cosmos {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  overflow: hidden;
  z-index: 1;
}

.cosmic-nebula {
  position: absolute;
  top: 20%;
  left: 20%;
  width: 300px;
  height: 200px;
  background: radial-gradient(ellipse at center, 
    rgba(255, 255, 255, 0.1) 0%, 
    rgba(200, 200, 200, 0.05) 40%, 
    transparent 70%);
  border-radius: 50%;
  animation: nebula-drift 60s linear infinite;
  filter: blur(2px);
}

@keyframes nebula-drift {
  0% { transform: translateX(0) rotate(0deg); opacity: 0.3; }
  50% { transform: translateX(100px) rotate(180deg); opacity: 0.6; }
  100% { transform: translateX(0) rotate(360deg); opacity: 0.3; }
}

/* Asteroid Belt */
.asteroid-belt {
  position: absolute;
  top: -50px;
  left: -50px;
  right: -50px;
  bottom: -50px;
}

.asteroid {
  position: absolute;
  width: 4px;
  height: 4px;
  background: #888888;
  border-radius: 50%;
  animation: asteroid-orbit 20s linear infinite;
}

.asteroid:nth-child(1) { 
  top: 20%; left: 50%; 
  animation-delay: 0s; 
  animation-duration: 18s;
}
.asteroid:nth-child(2) { 
  top: 35%; left: 80%; 
  animation-delay: -2s; 
  animation-duration: 22s;
}
.asteroid:nth-child(3) { 
  top: 65%; left: 80%; 
  animation-delay: -4s; 
  animation-duration: 19s;
}
.asteroid:nth-child(4) { 
  top: 80%; left: 50%; 
  animation-delay: -6s; 
  animation-duration: 21s;
}
.asteroid:nth-child(5) { 
  top: 65%; left: 20%; 
  animation-delay: -8s; 
  animation-duration: 20s;
}
.asteroid:nth-child(6) { 
  top: 35%; left: 20%; 
  animation-delay: -10s; 
  animation-duration: 23s;
}
.asteroid:nth-child(7) { 
  top: 50%; left: 90%; 
  animation-delay: -12s; 
  animation-duration: 17s;
}
.asteroid:nth-child(8) { 
  top: 50%; left: 10%; 
  animation-delay: -14s; 
  animation-duration: 24s;
}

@keyframes asteroid-orbit {
  0% { transform: rotate(0deg) translateX(80px) rotate(0deg); }
  100% { transform: rotate(360deg) translateX(80px) rotate(-360deg); }
}

/* Space Station */
.space-station {
  position: absolute;
  top: 40%;
  left: 5%;
  width: 60px;
  height: 60px;
  animation: station-rotate 50s linear infinite;
}

.station-module {
  position: absolute;
  width: 12px;
  height: 12px;
  background: #999999;
  border: 1px solid #666666;
}

.station-module:nth-child(1) { top: 0; left: 24px; }
.station-module:nth-child(2) { top: 24px; left: 48px; }
.station-module:nth-child(3) { top: 48px; left: 24px; }
.station-module:nth-child(4) { top: 24px; left: 0; }

@keyframes station-rotate {
  0% { transform: rotate(0deg) translateX(100px) rotate(0deg); }
  100% { transform: rotate(360deg) translateX(100px) rotate(-360deg); }
}

/* Responsive Cosmic Adjustments */
@media (max-width: 768px) {
  .planet-1, .planet-2, .planet-3 {
    width: 50px !important;
    height: 50px !important;
  }
  
  .cosmic-nebula {
    width: 200px;
    height: 120px;
  }
  
  .orbital-path {
    width: 150px;
    height: 150px;
    margin: -75px 0 0 -75px;
  }
  
  .space-station {
    width: 40px;
    height: 40px;
  }
  
  .station-module {
    width: 8px;
    height: 8px;
  }
}

/* ===== ENTREPRENEURSHIP TRIANGLE SECTION ===== */
.triangle-section {
  background: radial-gradient(circle at center, #0a0a1a, #000000);
  padding: 10rem 0;
  position: relative;
  overflow: hidden;
}

.triangle-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: 
    radial-gradient(circle at 20% 30%, rgba(100, 200, 255, 0.1) 0%, transparent 40%),
    radial-gradient(circle at 80% 70%, rgba(0, 255, 136, 0.1) 0%, transparent 40%);
  z-index: 1;
}

.triangle-container {
  max-width: 1000px;
  margin: 0 auto;
  position: relative;
  z-index: 10;
}

.entrepreneurship-triangle {
  position: relative;
  width: 100%;
  max-width: 700px;
  margin: 0 auto 6rem;
  height: 500px;
}

.triangle-svg {
  position: absolute;
  top: 50px;
  left: 50%;
  transform: translateX(-50%);
  width: 500px;
  height: 433px;
  z-index: 5;
  filter: drop-shadow(0 0 20px rgba(100, 200, 255, 0.6));
}

.triangle-svg path {
  animation: triangle-draw 4s ease-in-out infinite;
  stroke: #64c8ff;
  stroke-width: 3;
  fill: none;
  filter: drop-shadow(0 0 10px rgba(100, 200, 255, 0.8));
}

@keyframes triangle-draw {
  0%, 100% { 
    stroke-opacity: 0.7; 
    stroke-width: 3; 
    stroke-dasharray: 0, 1000;
  }
  50% { 
    stroke-opacity: 1; 
    stroke-width: 4; 
    stroke-dasharray: 500, 500;
  }
}

/* Vertices */
.vertex {
  position: absolute;
  background: #ffffff;
  border: 2px solid #000000;
  border-radius: 15px;
  padding: 1.5rem;
  text-align: center;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  z-index: 10;
  min-width: 120px;
}

.vertex:hover {
  transform: translateY(-5px) scale(1.05);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
  border-color: #333333;
}

.tech-vertex {
  top: 0;
  left: 50%;
  transform: translateX(-50%);
}

.finance-vertex {
  bottom: 0;
  left: 0;
}

.marketing-vertex {
  bottom: 0;
  right: 0;
}

.vertex-icon {
  font-size: 2rem;
  margin-bottom: 0.5rem;
}

.vertex-label {
  font-weight: var(--font-weight-bold);
  font-size: 0.875rem;
  color: #000000;
  margin-bottom: 0.5rem;
  letter-spacing: 0.1em;
}

.vertex-description {
  font-size: 0.75rem;
  color: #666666;
  line-height: 1.4;
}

/* Center Point */
.center-point {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: #000000;
  color: #ffffff;
  border-radius: 20px;
  padding: 2rem;
  text-align: center;
  cursor: pointer;
  transition: all 0.3s ease;
  z-index: 15;
  min-width: 180px;
}

.center-point:hover {
  transform: translate(-50%, -50%) scale(1.1);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
}

.center-icon {
  font-size: 2.5rem;
  margin-bottom: 0.75rem;
  animation: rocket-pulse 2s ease-in-out infinite;
}

@keyframes rocket-pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.1); }
}

.center-label {
  font-weight: var(--font-weight-bold);
  font-size: 1rem;
  margin-bottom: 0.75rem;
  letter-spacing: 0.05em;
}

.center-description {
  font-size: 0.875rem;
  color: #cccccc;
  line-height: 1.4;
}

.energy-pulse {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 100%;
  height: 100%;
  border: 2px solid #ffffff;
  border-radius: 20px;
  transform: translate(-50%, -50%);
  animation: energy-pulse-animation 3s ease-in-out infinite;
  opacity: 0.3;
}

@keyframes energy-pulse-animation {
  0%, 100% { transform: translate(-50%, -50%) scale(1); opacity: 0.3; }
  50% { transform: translate(-50%, -50%) scale(1.2); opacity: 0.1; }
}

/* Connection Lines */
.connection-lines {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 5;
}

.line {
  position: absolute;
  background: linear-gradient(45deg, transparent, #000000, transparent);
  opacity: 0;
  animation: connection-pulse 4s ease-in-out infinite;
}

.tech-to-center {
  top: 25%;
  left: 50%;
  width: 2px;
  height: 25%;
  transform: translateX(-50%);
  animation-delay: 0s;
}

.finance-to-center {
  bottom: 25%;
  left: 25%;
  width: 25%;
  height: 2px;
  transform: rotate(60deg);
  transform-origin: left center;
  animation-delay: 1s;
}

.marketing-to-center {
  bottom: 25%;
  right: 25%;
  width: 25%;
  height: 2px;
  transform: rotate(-60deg);
  transform-origin: right center;
  animation-delay: 2s;
}

@keyframes connection-pulse {
  0%, 70%, 100% { opacity: 0; }
  35% { opacity: 0.6; }
}

/* Skills Breakdown */
.skills-breakdown {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  margin-top: 4rem;
}

.skill-category {
  background: #fafafa;
  border: 1px solid #e9ecef;
  border-radius: 15px;
  padding: 2rem;
  transition: all 0.3s ease;
}

.skill-category:hover {
  transform: translateY(-3px);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.1);
  border-color: #000000;
}

.skill-category h3 {
  font-size: 1.25rem;
  font-weight: var(--font-weight-bold);
  margin-bottom: 1.5rem;
  color: #000000;
}

.skill-category ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.skill-category li {
  padding: 0.5rem 0;
  color: #666666;
  border-bottom: 1px solid #f0f0f0;
  font-size: 0.875rem;
}

.skill-category li:last-child {
  border-bottom: none;
}

.skill-category li:before {
  content: "▶";
  color: #000000;
  margin-right: 0.75rem;
  font-size: 0.75rem;
}

/* ===== BUSINESS MINDSET SECTION ===== */
.mindset-section {
  background: #fafafa;
  padding: 8rem 0;
}

.mindset-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
}

.mindset-card {
  background: #ffffff;
  border: 1px solid #e9ecef;
  border-radius: 20px;
  padding: 2.5rem;
  transition: all 0.3s ease;
  cursor: pointer;
  position: relative;
  overflow: hidden;
}

.mindset-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.15);
  border-color: #000000;
}

.mindset-icon {
  font-size: 3rem;
  margin-bottom: 1.5rem;
  display: block;
}

.mindset-content {
  position: relative;
  z-index: 2;
}

.mindset-title {
  font-size: 1.5rem;
  font-weight: var(--font-weight-bold);
  margin-bottom: 1rem;
  color: #000000;
}

.mindset-description {
  color: #666666;
  line-height: 1.6;
  margin-bottom: 1.5rem;
}

.mindset-example {
  background: #f8f9fa;
  padding: 1rem;
  border-radius: 10px;
  font-size: 0.875rem;
  color: #495057;
  border-left: 4px solid #000000;
}

/* ===== BLOG SECTION ===== */
.blog-section {
  background: #ffffff;
  padding: 8rem 0;
}

.blog-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
  margin-bottom: 4rem;
}

.blog-card {
  background: #fafafa;
  border: 1px solid #e9ecef;
  border-radius: 20px;
  padding: 2rem;
  transition: all 0.3s ease;
  cursor: pointer;
  position: relative;
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

.blog-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.12);
  border-color: #000000;
}

.blog-meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1.5rem;
}

.blog-category {
  background: #000000;
  color: #ffffff;
  padding: 0.25rem 0.75rem;
  border-radius: 15px;
  font-size: 0.75rem;
  font-weight: var(--font-weight-semibold);
}

.blog-date {
  color: #666666;
  font-size: 0.875rem;
  font-family: var(--font-family-mono);
}

.blog-content {
  flex: 1;
  margin-bottom: 1.5rem;
}

.blog-title {
  font-size: 1.25rem;
  font-weight: var(--font-weight-bold);
  margin-bottom: 1rem;
  color: #000000;
  line-height: 1.3;
}

.blog-excerpt {
  color: #666666;
  line-height: 1.6;
  margin-bottom: 1.5rem;
}

.blog-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.tag {
  background: #f0f0f0;
  color: #666666;
  padding: 0.25rem 0.5rem;
  border-radius: 8px;
  font-size: 0.75rem;
  transition: all 0.3s ease;
}

.blog-card:hover .tag {
  background: #e0e0e0;
}

.blog-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: 1rem;
  border-top: 1px solid #e9ecef;
}

.read-time {
  color: #999999;
  font-size: 0.875rem;
  font-family: var(--font-family-mono);
}

.read-more {
  color: #000000;
  text-decoration: none;
  font-weight: var(--font-weight-semibold);
  font-size: 0.875rem;
  transition: all 0.3s ease;
}

.read-more:hover {
  color: #333333;
  transform: translateX(3px);
}

.blog-link {
  text-align: center;
  margin-top: 3rem;
}

/* Responsive Design */
@media (max-width: 768px) {
  .triangle-section {
    padding: 6rem 0;
  }
  
  .entrepreneurship-triangle {
    height: 300px;
    margin-bottom: 4rem;
  }
  
  .triangle-svg {
    width: 300px;
    height: 260px;
  }
  
  .vertex {
    padding: 1rem;
    min-width: 100px;
  }
  
  .center-point {
    padding: 1.5rem;
    min-width: 140px;
  }
  
  .vertex-icon {
    font-size: 1.5rem;
  }
  
  .center-icon {
    font-size: 2rem;
  }
  
  .vertex-label {
    font-size: 0.75rem;
  }
  
  .vertex-description {
    font-size: 0.7rem;
  }
  
  .skills-breakdown {
    grid-template-columns: 1fr;
    margin-top: 3rem;
  }
  
  .mindset-grid,
  .blog-grid {
    grid-template-columns: 1fr;
  }
  
  .mindset-card,
  .blog-card {
    padding: 1.5rem;
  }
}

/* Reduce motion for cosmic effects */
@media (prefers-reduced-motion: reduce) {
  .magical-shape, .particle-trail, .trail-dot, .energy-wave,
  .planet, .orbital-path, .orbiting-object, .cosmic-nebula,
  .asteroid, .space-station, .glitch-text, .typewriter-text,
  .triangle-svg, .center-icon, .energy-pulse, .line {
    animation: none !important;
    opacity: 0.3 !important;
  }
  
  .typewriter-text {
    border-right: none !important;
    width: auto !important;
  }
}
</style> 