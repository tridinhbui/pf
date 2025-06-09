<template>
  <div class="portfolio">
    <!-- Animated Background -->
    <AnimatedBackground />
    
    <!-- Galaxy Background -->
    <div class="galaxy-background">
      <div class="cosmic-nebula">
        <div class="nebula-cloud" v-for="n in 8" :key="`nebula-${n}`"></div>
      </div>
      <div class="stellar-field">
        <div class="star-layer">
          <div class="star" v-for="n in 200" :key="`star-${n}`"></div>
        </div>
        <div class="constellation-lines">
          <svg class="constellation-svg" viewBox="0 0 1920 1080">
            <g class="constellation-group" v-for="n in 5" :key="`constellation-${n}`">
              <line class="constellation-line" x1="100" y1="100" x2="200" y2="150" />
              <line class="constellation-line" x1="200" y1="150" x2="300" y2="120" />
              <line class="constellation-line" x1="300" y1="120" x2="380" y2="180" />
              <circle class="constellation-star" cx="100" cy="100" r="2" />
              <circle class="constellation-star" cx="200" cy="150" r="3" />
              <circle class="constellation-star" cx="300" cy="120" r="2" />
              <circle class="constellation-star" cx="380" cy="180" r="4" />
            </g>
          </svg>
        </div>
      </div>
      <div class="cosmic-dust">
        <div class="dust-particle" v-for="n in 100" :key="`dust-${n}`"></div>
      </div>
      <div class="quantum-field">
        <div class="quantum-dot" v-for="n in 50" :key="`quantum-${n}`"></div>
      </div>
    </div>
    
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

    <!-- Welcome Popup -->
    <div class="welcome-popup" v-if="showWelcomePopup" @click="closeWelcomePopup">
      <div class="popup-overlay"></div>
      <div class="popup-content" @click.stop>
        <div class="popup-header">
          <div class="hologram-effect">
            <div class="hologram-text">WELCOME TO THE ECOSYSTEM</div>
            <div class="hologram-scan"></div>
          </div>
        </div>
        
        <div class="popup-body">
          <div class="matrix-rain">
            <div class="rain-column" v-for="n in 20" :key="n">
              <span v-for="char in matrixChars" :key="char">{{ char }}</span>
            </div>
          </div>
          
          <div class="welcome-message">
            <h2 class="cosmic-title">
              <span class="glitch-effect" data-text="TRI BUI">TRI BUI</span>
            </h2>
            <p class="subtitle">Ecosystem Builder • Strategic Innovator • Future Creator</p>
            <div class="tech-specs">
              <div class="spec-line">
                <span class="label">STATUS:</span>
                <span class="value typing-effect">ONLINE</span>
              </div>
              <div class="spec-line">
                <span class="label">MODE:</span>
                <span class="value typing-effect">INNOVATION</span>
              </div>
              <div class="spec-line">
                <span class="label">MISSION:</span>
                <span class="value typing-effect">TRANSFORMING FUTURES</span>
              </div>
            </div>
          </div>
        </div>
        
        <div class="popup-footer">
          <button class="enter-btn" @click="closeWelcomePopup">
            <span>ENTER THE ECOSYSTEM</span>
            <div class="btn-glow"></div>
          </button>
        </div>
        
        <button class="close-btn" @click="closeWelcomePopup">×</button>
      </div>
    </div>
    
    <!-- Navigation Bar -->
    <NavBar />
    
    <!-- Magnetic Cursor -->
    <MagneticCursor />
    
    <!-- Hero Section -->
    <section class="section hero-section galaxy-section">
      <div class="visionary-overlay">
        <div class="holographic-grid">
          <div class="grid-line" v-for="n in 20" :key="`h-grid-${n}`"></div>
          <div class="grid-line vertical" v-for="n in 20" :key="`v-grid-${n}`"></div>
        </div>
        <div class="data-streams">
          <div class="data-stream" v-for="n in 6" :key="`stream-${n}`">
            <div class="data-packet" v-for="p in 8" :key="`packet-${p}`"></div>
          </div>
        </div>
        <div class="cosmic-portals">
          <div class="portal" v-for="n in 3" :key="`portal-${n}`">
            <div class="portal-ring" v-for="ring in 5" :key="ring"></div>
            <div class="portal-core"></div>
          </div>
        </div>
      </div>
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
            <!-- Professional Profile Image -->
            <div class="profile-image-container">
              <img src="@/assets/tri1.png" alt="Tri Bui - Entrepreneur & Builder" class="profile-image" />
              <div class="profile-glow"></div>
            </div>
            
            <h1 class="hero-title professional-title cosmic-text galaxy-title">
              <span class="title-main glitch-text shake-interval visionary-text" data-text="I don't just build startups.">I don't just build startups.</span>
              <br>
              <span class="title-sub strong-emphasis typewriter-text galactic-emphasis">I build ecosystems.</span>
            </h1>
            <p class="hero-subtitle professional-subtitle">
              I'm a strategist and builder focused on creating everlasting impact through innovative platforms that reshape how the next generation thinks, builds, and conquers.
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
          
          <!-- Journey Image -->
          <div class="journey-image-container">
            <img src="@/assets/tri2.png" alt="Educational Journey - From Hanoi to Global Impact" class="journey-image" />
            <div class="journey-overlay">
              <span class="journey-caption">Hanoi → Minnesota → Singapore → Chicago → Virginia</span>
            </div>
          </div>
        </div>
        
        <div class="origin-content">
          <div class="origin-grid">
            <div class="origin-item" ref="originItem1">
              <div class="origin-label">Launch vector</div>
              <div class="origin-value">Hanoi ➜ Minnesota (Macalester) ➜ Singapore (NTU exchange) ➜ Chicago ➜ Virginia (Smithfield HQ)</div>
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

    <!-- INSANE BUSINESS TRANSFORMATION SECTION -->
    <section class="section transformation-chaos-section">
      <div class="transformation-container">
        <!-- Chaotic Background Effects -->
        <div class="chaos-bg">
          <div class="lightning-bolts">
            <div class="lightning" v-for="n in 12" :key="`lightning-${n}`"></div>
          </div>
          <div class="data-explosions">
            <div class="explosion" v-for="n in 8" :key="`explosion-${n}`">
              <div class="explosion-ring" v-for="ring in 5" :key="ring"></div>
            </div>
          </div>
          <div class="fractal-patterns">
            <div class="fractal" v-for="n in 6" :key="`fractal-${n}`">
              <div class="fractal-branch" v-for="branch in 8" :key="branch"></div>
            </div>
          </div>
        </div>
        
        <!-- Central Transformation Core -->
        <div class="transformation-core">
          <div class="core-title">
            <span class="chaos-text" data-text="BUSINESS">BUSINESS</span>
            <span class="chaos-text" data-text="TRANSFORMATION">TRANSFORMATION</span>
            <span class="chaos-text" data-text="REVOLUTION">REVOLUTION</span>
          </div>
          
          <div class="transformation-manifesto">
            <div class="manifesto-line">
              <span class="keyword">DISRUPT</span> → Traditional Models
            </div>
            <div class="manifesto-line">
              <span class="keyword">REBUILD</span> → Sustainable Systems
            </div>
            <div class="manifesto-line">
              <span class="keyword">ACCELERATE</span> → Future Growth
            </div>
          </div>
        </div>
        
        <!-- Transformation Pillars -->
        <div class="transformation-pillars">
          <div class="pillar" v-for="(pillar, index) in transformationPillars" :key="pillar.id">
            <div class="pillar-energy">
              <div class="energy-core"></div>
              <div class="energy-pulse" v-for="n in 3" :key="n"></div>
            </div>
            <div class="pillar-content">
              <div class="pillar-icon">{{ pillar.icon }}</div>
              <h3 class="pillar-title">{{ pillar.title }}</h3>
              <p class="pillar-description">{{ pillar.description }}</p>
              <div class="pillar-impact">{{ pillar.impact }}</div>
            </div>
            <div class="pillar-chaos-overlay">
              <div class="chaos-particle" v-for="n in 15" :key="n"></div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- INSANE CHAOS SECTION -->
    <section class="section chaos-section">
      <div class="chaos-container">
        <!-- Chaos Background -->
        <div class="chaos-background">
          <div class="chaos-grid">
            <div class="grid-chaos-line" v-for="n in 20" :key="`chaos-h-${n}`"></div>
            <div class="grid-chaos-line vertical" v-for="n in 20" :key="`chaos-v-${n}`"></div>
          </div>
          
          <!-- Flying Objects -->
          <div class="flying-objects">
            <div class="flying-cube" v-for="n in 15" :key="`cube-${n}`">
              <div class="cube-face" v-for="face in 6" :key="face"></div>
            </div>
            <div class="flying-sphere" v-for="n in 10" :key="`sphere-${n}`">
              <div class="sphere-core"></div>
              <div class="sphere-ring" v-for="ring in 3" :key="ring"></div>
            </div>
            <div class="flying-pyramid" v-for="n in 8" :key="`pyramid-${n}`">
              <div class="pyramid-face" v-for="face in 4" :key="face"></div>
            </div>
          </div>
          
          <!-- Wormholes -->
          <div class="wormholes">
            <div class="wormhole" v-for="n in 4" :key="`wormhole-${n}`">
              <div class="wormhole-ring" v-for="ring in 8" :key="ring"></div>
              <div class="wormhole-core"></div>
            </div>
          </div>
          
          <!-- Energy Beams -->
          <div class="energy-beams">
            <div class="energy-beam" v-for="n in 6" :key="`beam-${n}`">
              <div class="beam-core"></div>
              <div class="beam-particles">
                <div class="beam-particle" v-for="p in 20" :key="p"></div>
              </div>
            </div>
          </div>
        </div>
        
        <!-- Central Chaos Message -->
        <div class="chaos-message">
          <div class="chaos-title">
            <span class="chaos-word" v-for="(word, index) in chaosWords" :key="word" :style="{ '--word-delay': index * 0.2 + 's' }">
              {{ word }}
            </span>
          </div>
          <div class="chaos-subtitle">
            Where innovation meets absolute madness
          </div>
        </div>
        
        <!-- Floating Code Matrix -->
        <div class="code-matrix">
          <div class="code-stream" v-for="n in 8" :key="`stream-${n}`">
            <div class="code-char" v-for="char in randomChars.slice(0, 15)" :key="char.id">{{ char.value }}</div>
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
          
          <!-- Entrepreneurial Impact Image -->
          <div class="ventures-image-container">
            <img src="@/assets/tri3.png" alt="Entrepreneurial Ventures & Impact" class="ventures-image" />
            <div class="ventures-stats">
              <div class="stat-item">
                <span class="stat-number">5</span>
                <span class="stat-label">Ventures Founded</span>
              </div>
              <div class="stat-item">
                <span class="stat-number">350+</span>
                <span class="stat-label">Lives Impacted</span>
              </div>
              <div class="stat-item">
                <span class="stat-number">12K+</span>
                <span class="stat-label">Users Reached</span>
              </div>
            </div>
          </div>
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

    <!-- Power Quote Section -->
    <section class="section quote-power-section">
      <div class="container">
        <div class="power-quote-container" ref="powerQuoteRef">
          <div class="quote-background-stars">
            <div class="star" v-for="n in 50" :key="`quote-star-${n}`"></div>
          </div>
          <blockquote class="power-quote">
            <span class="quote-highlight">"Finance and Technology"</span> are the disciplined foundations I've forged through relentless training, 
            while <span class="quote-highlight">"Marketing"</span> flows as my natural-born instinct.
          </blockquote>
          <div class="quote-author">— Tri Bui</div>
        </div>
      </div>
    </section>

    <!-- Business Mindset Section -->
    <section class="section mindset-section" id="mindset">
      <div class="container">
        <div class="section-header">
          <h2 class="section-title mindset-title-white" ref="mindsetTitleRef">Business & Entrepreneurship Mindset</h2>
          <p class="section-subtitle">Core principles that drive innovation and sustainable growth</p>
          <div class="mindset-stars-background">
            <div class="mindset-star" v-for="n in 30" :key="`mindset-star-${n}`"></div>
          </div>
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

    <!-- Enhanced Starry Background with Multiple Particle Effects -->
    <div class="starry-background">
      <!-- Main stars -->
      <div class="star" v-for="n in 80" :key="`star-${n}`" :style="generateStarStyle()"></div>
      
      <!-- Floating particles -->
      <div class="floating-particle" v-for="n in 30" :key="`particle-${n}`" :style="generateParticleStyle()"></div>
      
      <!-- Nebula clouds -->
      <div class="nebula-cloud" v-for="n in 5" :key="`nebula-${n}`" :style="generateNebulaStyle()"></div>
      
      <!-- Shooting stars -->
      <div class="shooting-star" v-for="n in 3" :key="`shooting-${n}`" :style="generateShootingStarStyle()"></div>
    </div>
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
  },
  {
    id: 7,
    icon: "🔄",
    title: "Business Transformation",
    description: "Leading organizational change through digital innovation and process optimization.",
    example: "Transformed traditional SME operations with Esmart Solution's data-driven approach."
  },
  {
    id: 8,
    icon: "🌱",
    title: "Sustainable Startup Building",
    description: "Creating ventures that balance profit with social impact and environmental responsibility.",
    example: "CF Hub's mentorship model ensures 78% job placement rate while maintaining ethical practices."
  },
  {
    id: 9,
    icon: "👥",
    title: "Team Leadership & Development",
    description: "Building high-performing teams through mentorship, clear vision, and continuous learning.",
    example: "Developed 25+ mentors across 3 continents, creating a distributed leadership network."
  },
  {
    id: 10,
    icon: "🎓",
    title: "Sustainable Human Development",
    description: "Investing in long-term talent development and creating pathways for continuous growth.",
    example: "Pathwise alumni have 92% career advancement rate within 2 years of program completion."
  }
])

const chaosWords = ref(['CHAOS', 'INNOVATION', 'DISRUPTION', 'REVOLUTION', 'TRANSFORMATION'])

// Welcome popup state
const showWelcomePopup = ref(true)
const matrixChars = ['0', '1', 'T', 'R', 'I', 'B', 'U', 'I', '█', '▓', '░', '╔', '╗', '╚', '╝']

// Transformation pillars data
const transformationPillars = ref([
  {
    id: 1,
    icon: '⚡',
    title: 'Digital Disruption',
    description: 'Shattering traditional business models with AI-driven innovation',
    impact: '300% efficiency gains achieved'
  },
  {
    id: 2,
    icon: '🔥',
    title: 'Ecosystem Revolution',
    description: 'Building interconnected platforms that create exponential value',
    impact: '1000+ stakeholders connected'
  },
  {
    id: 3,
    icon: '💎',
    title: 'Strategic Metamorphosis',
    description: 'Transforming companies into future-ready powerhouses',
    impact: '$50M+ value unlocked'
  },
  {
    id: 4,
    icon: '🚀',
    title: 'Growth Acceleration',
    description: 'Scaling startups from 0 to unicorn status',
    impact: '10x growth multiplier'
  }
])

// Functions for popup
const closeWelcomePopup = () => {
  showWelcomePopup.value = false
}

// Define a type for the characters in the matrix effect
interface MatrixChar {
  id: number;
  value: string;
}

// Initialize randomChars with the correct type
const randomChars = ref<MatrixChar[]>([]);

// Generate random characters for matrix effect
const generateRandomChars = () => {
  const chars = '01アイウエオカキクケコサシスセソタチツテトナニヌネノハヒフヘホマミムメモヤユヨラリルレロワヲン'
  const result = []
  for (let i = 0; i < 200; i++) {
    result.push({
      id: i,
      value: chars[Math.floor(Math.random() * chars.length)]
    })
  }
  return result
}

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
  setTimeout(setupGalaxyEffects, 500) // Delay to ensure DOM is ready
  randomChars.value = generateRandomChars()
  
  // Update random chars every 300ms for matrix effect (reduced frequency for better performance)
  setInterval(() => {
    randomChars.value = generateRandomChars()
  }, 300)
  
  // Add mouse move effect for interactive particles
  const handleMouseMove = (event: MouseEvent) => {
    const particles = document.querySelectorAll('.floating-particle')
    const mouseX = event.clientX / window.innerWidth
    const mouseY = event.clientY / window.innerHeight
    
    particles.forEach((particle, index) => {
      const element = particle as HTMLElement
      const offsetX = (mouseX - 0.5) * (20 + index * 2)
      const offsetY = (mouseY - 0.5) * (20 + index * 2)
      element.style.transform = `translate3d(${offsetX}px, ${offsetY}px, 0) scale(${1 + mouseX * 0.2})`
    })
  }
  
  document.addEventListener('mousemove', handleMouseMove)
})

const setupGalaxyEffects = () => {
  // Position stars randomly
  const stars = document.querySelectorAll('.star')
  stars.forEach((star: Element, index: number) => {
    const element = star as HTMLElement
    const x = Math.random() * 100
    const y = Math.random() * 100
    const size = Math.random() * 3 + 1
    const delay = Math.random() * 3
    
    element.style.left = `${x}vw`
    element.style.top = `${y}vh`
    element.style.width = `${size}px`
    element.style.height = `${size}px`
    element.style.animationDelay = `${delay}s`
  })

  // Position dust particles randomly
  const dustParticles = document.querySelectorAll('.dust-particle')
  dustParticles.forEach((particle: Element, index: number) => {
    const element = particle as HTMLElement
    const x = Math.random() * 100
    const delay = Math.random() * 15
    
    element.style.left = `${x}vw`
    element.style.animationDelay = `${delay}s`
  })

  // Position quantum dots randomly
  const quantumDots = document.querySelectorAll('.quantum-dot')
  quantumDots.forEach((dot: Element, index: number) => {
    const element = dot as HTMLElement
    const x = Math.random() * 100
    const y = Math.random() * 100
    const delay = Math.random() * 2
    
    element.style.left = `${x}vw`
    element.style.top = `${y}vh`
    element.style.animationDelay = `${delay}s`
  })
}

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

// Function to generate random star styles with improved variety
function generateStarStyle() {
  const x = Math.random() * 100;
  const y = Math.random() * 100;
  const delay = Math.random() * 15;
  const size = Math.random() * 4 + 1;
  const brightness = Math.random() * 0.8 + 0.2;
  const speed = Math.random() * 5 + 8;
  return {
    left: `${x}vw`,
    top: `${y}vh`,
    animationDelay: `-${delay}s`,
    animationDuration: `${speed}s`,
    width: `${size}px`,
    height: `${size}px`,
    opacity: brightness
  };
}

// Function to generate floating particle styles with enhanced variety
function generateParticleStyle() {
  const x = Math.random() * 100;
  const y = Math.random() * 100;
  const delay = Math.random() * 20;
  const duration = Math.random() * 15 + 10;
  const size = Math.random() * 6 + 2;
  const hue = Math.random() * 60 + 120; // Green to cyan range
  return {
    left: `${x}vw`,
    top: `${y}vh`,
    animationDelay: `-${delay}s`,
    animationDuration: `${duration}s`,
    width: `${size}px`,
    height: `${size}px`,
    filter: `hue-rotate(${hue}deg)`
  };
}

// Function to generate nebula cloud styles
function generateNebulaStyle() {
  const x = Math.random() * 100;
  const y = Math.random() * 100;
  const delay = Math.random() * 20;
  const size = Math.random() * 200 + 100;
  return {
    left: `${x}vw`,
    top: `${y}vh`,
    animationDelay: `-${delay}s`,
    width: `${size}px`,
    height: `${size}px`
  };
}

// Function to generate shooting star styles with enhanced trails
function generateShootingStarStyle() {
  const x = Math.random() * 100;
  const y = Math.random() * 40;
  const delay = Math.random() * 25;
  const duration = Math.random() * 3 + 6;
  const brightness = Math.random() * 0.5 + 0.5;
  const trailLength = Math.random() * 100 + 50;
  return {
    left: `${x}vw`,
    top: `${y}vh`,
    animationDelay: `-${delay}s`,
    animationDuration: `${duration}s`,
    opacity: brightness,
    '--trail-length': `${trailLength}px`
  };
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
  transition: all 0.3s ease;
  will-change: transform;
  background: rgba(0, 0, 0, 0.1);
  backdrop-filter: blur(10px);
  border-top: 1px solid rgba(135, 206, 235, 0.1);
  border-bottom: 1px solid rgba(138, 43, 226, 0.1);
}

.section:hover {
  transform: scale3d(1.01, 1.01, 1);
  box-shadow: 
    0 20px 40px rgba(138, 43, 226, 0.2),
    0 0 60px rgba(135, 206, 235, 0.1),
    inset 0 0 30px rgba(255, 255, 255, 0.05);
  background: rgba(10, 10, 46, 0.15);
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
  background: linear-gradient(45deg, #87ceeb 0%, #dda0dd 50%, #ffd700 100%);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  text-shadow: 0 0 30px rgba(135, 206, 235, 0.5);
  animation: cosmic-glow 3s ease-in-out infinite;
}

@keyframes cosmic-glow {
  0%, 100% { filter: brightness(1) drop-shadow(0 0 10px rgba(135, 206, 235, 0.3)); }
  50% { filter: brightness(1.3) drop-shadow(0 0 25px rgba(221, 160, 221, 0.5)); }
}

/* Galaxy Title Styling */
.galaxy-title {
  color: #ffffff;
  text-shadow: 
    0 0 20px rgba(135, 206, 235, 0.6),
    0 0 40px rgba(138, 43, 226, 0.4),
    0 0 60px rgba(255, 215, 0, 0.3);
}

.visionary-text {
  background: linear-gradient(45deg, #87ceeb 0%, #dda0dd 30%, #ffd700 60%, #87ceeb 100%);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-size: 200% 200%;
  animation: visionary-flow 4s ease-in-out infinite;
}

@keyframes visionary-flow {
  0%, 100% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
}

.galactic-emphasis {
  background: linear-gradient(135deg, #ff00ff 0%, #00ffff 50%, #ffff00 100%);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  text-shadow: 
    0 0 30px rgba(255, 0, 255, 0.5),
    0 0 50px rgba(0, 255, 255, 0.3);
  animation: galactic-pulse 2s ease-in-out infinite;
}

@keyframes galactic-pulse {
  0%, 100% { transform: scale(1); filter: brightness(1); }
  50% { transform: scale(1.05); filter: brightness(1.3); }
}

.section-subtitle {
  font-size: 1.25rem;
  color: #666666;
  font-style: italic;
  max-width: 600px;
  margin: 0 auto;
}

/* ===== GALAXY BACKGROUND ===== */
.galaxy-background {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  pointer-events: none;
  z-index: -1;
  overflow: hidden;
}

/* Cosmic Nebula */
.cosmic-nebula {
  position: absolute;
  width: 100%;
  height: 100%;
}

.nebula-cloud {
  position: absolute;
  border-radius: 50%;
  background: radial-gradient(circle, 
    rgba(138, 43, 226, 0.3) 0%, 
    rgba(75, 0, 130, 0.2) 30%, 
    rgba(25, 25, 112, 0.1) 60%, 
    transparent 100%);
  animation: nebula-drift 20s ease-in-out infinite;
}

.nebula-cloud:nth-child(1) { width: 400px; height: 300px; top: 10%; left: 10%; animation-delay: 0s; }
.nebula-cloud:nth-child(2) { width: 600px; height: 400px; top: 60%; right: 15%; animation-delay: 3s; }
.nebula-cloud:nth-child(3) { width: 350px; height: 250px; top: 80%; left: 70%; animation-delay: 6s; }
.nebula-cloud:nth-child(4) { width: 500px; height: 350px; top: 20%; right: 40%; animation-delay: 9s; }
.nebula-cloud:nth-child(5) { width: 450px; height: 300px; top: 40%; left: 60%; animation-delay: 12s; }
.nebula-cloud:nth-child(6) { width: 300px; height: 200px; top: 70%; left: 20%; animation-delay: 15s; }
.nebula-cloud:nth-child(7) { width: 550px; height: 380px; top: 30%; right: 10%; animation-delay: 18s; }
.nebula-cloud:nth-child(8) { width: 400px; height: 280px; bottom: 10%; left: 50%; animation-delay: 21s; }

@keyframes nebula-drift {
  0%, 100% { transform: translate(0, 0) scale(1); opacity: 0.3; }
  33% { transform: translate(20px, -15px) scale(1.1); opacity: 0.5; }
  66% { transform: translate(-15px, 20px) scale(0.9); opacity: 0.4; }
}

/* Stellar Field */
.stellar-field {
  position: absolute;
  width: 100%;
  height: 100%;
}

.star-layer {
  position: absolute;
  width: 100%;
  height: 100%;
}

.star {
  position: absolute;
  background: radial-gradient(circle, #ffffff 0%, transparent 70%);
  border-radius: 50%;
  animation: stellar-twinkle 3s ease-in-out infinite;
}

.star:nth-child(odd) {
  background: radial-gradient(circle, #87ceeb 0%, transparent 70%);
}

.star:nth-child(3n) {
  background: radial-gradient(circle, #dda0dd 0%, transparent 70%);
}

.star:nth-child(5n) {
  background: radial-gradient(circle, #ffd700 0%, transparent 70%);
}

@keyframes stellar-twinkle {
  0%, 100% { opacity: 0.3; transform: scale(1); }
  50% { opacity: 1; transform: scale(1.2); }
}

/* Constellation Lines */
.constellation-lines {
  position: absolute;
  width: 100%;
  height: 100%;
  opacity: 0.4;
}

.constellation-svg {
  width: 100%;
  height: 100%;
}

.constellation-group {
  animation: constellation-pulse 8s ease-in-out infinite;
}

.constellation-line {
  stroke: #87ceeb;
  stroke-width: 1;
  opacity: 0.6;
  animation: constellation-glow 4s ease-in-out infinite;
}

.constellation-star {
  fill: #ffffff;
  animation: star-pulse 2s ease-in-out infinite;
}

@keyframes constellation-pulse {
  0%, 100% { opacity: 0.3; }
  50% { opacity: 0.8; }
}

@keyframes constellation-glow {
  0%, 100% { stroke-opacity: 0.3; }
  50% { stroke-opacity: 0.8; stroke-width: 2; }
}

@keyframes star-pulse {
  0%, 100% { fill-opacity: 0.6; r: 2; }
  50% { fill-opacity: 1; r: 4; }
}

/* Cosmic Dust */
.cosmic-dust {
  position: absolute;
  width: 100%;
  height: 100%;
}

.dust-particle {
  position: absolute;
  width: 1px;
  height: 1px;
  background: rgba(255, 255, 255, 0.4);
  border-radius: 50%;
  animation: dust-float 15s linear infinite;
}

@keyframes dust-float {
  0% { transform: translateY(100vh) translateX(0); opacity: 0; }
  10% { opacity: 1; }
  90% { opacity: 1; }
  100% { transform: translateY(-100px) translateX(50px); opacity: 0; }
}

/* Quantum Field */
.quantum-field {
  position: absolute;
  width: 100%;
  height: 100%;
}

.quantum-dot {
  position: absolute;
  width: 2px;
  height: 2px;
  background: radial-gradient(circle, #00ffff 0%, transparent 70%);
  border-radius: 50%;
  animation: quantum-fluctuation 2s ease-in-out infinite;
}

@keyframes quantum-fluctuation {
  0%, 100% { opacity: 0; transform: scale(1); }
  50% { opacity: 1; transform: scale(3); }
}

/* Visionary Overlay */
.visionary-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 1;
}

/* Holographic Grid */
.holographic-grid {
  position: absolute;
  width: 100%;
  height: 100%;
  opacity: 0.1;
}

.holographic-grid .grid-line {
  position: absolute;
  background: linear-gradient(90deg, transparent, rgba(0, 255, 255, 0.3), transparent);
  height: 1px;
  width: 100%;
  animation: hologram-scan 4s linear infinite;
}

.holographic-grid .grid-line.vertical {
  width: 1px;
  height: 100%;
  background: linear-gradient(0deg, transparent, rgba(0, 255, 255, 0.3), transparent);
}

.holographic-grid .grid-line:nth-child(1) { top: 5%; animation-delay: 0s; }
.holographic-grid .grid-line:nth-child(2) { top: 15%; animation-delay: 0.5s; }
.holographic-grid .grid-line:nth-child(3) { top: 25%; animation-delay: 1s; }
.holographic-grid .grid-line:nth-child(4) { top: 35%; animation-delay: 1.5s; }
.holographic-grid .grid-line:nth-child(5) { top: 45%; animation-delay: 2s; }

@keyframes hologram-scan {
  0%, 100% { opacity: 0.1; }
  50% { opacity: 0.6; }
}

/* Data Streams */
.data-streams {
  position: absolute;
  width: 100%;
  height: 100%;
}

.data-stream {
  position: absolute;
  width: 2px;
  height: 100%;
  animation: data-flow 3s linear infinite;
}

.data-stream:nth-child(1) { left: 10%; animation-delay: 0s; }
.data-stream:nth-child(2) { left: 30%; animation-delay: 0.5s; }
.data-stream:nth-child(3) { left: 50%; animation-delay: 1s; }
.data-stream:nth-child(4) { left: 70%; animation-delay: 1.5s; }
.data-stream:nth-child(5) { left: 85%; animation-delay: 2s; }
.data-stream:nth-child(6) { right: 5%; animation-delay: 2.5s; }

.data-packet {
  width: 4px;
  height: 8px;
  background: linear-gradient(to bottom, #00ffff, #ff00ff);
  margin-bottom: 20px;
  border-radius: 2px;
  animation: packet-travel 2s ease-in-out infinite;
}

@keyframes data-flow {
  0% { transform: translateY(100vh); }
  100% { transform: translateY(-100px); }
}

@keyframes packet-travel {
  0%, 100% { opacity: 0.3; box-shadow: 0 0 5px #00ffff; }
  50% { opacity: 1; box-shadow: 0 0 15px #ff00ff, 0 0 25px #00ffff; }
}

/* Cosmic Portals */
.cosmic-portals {
  position: absolute;
  width: 100%;
  height: 100%;
}

.portal {
  position: absolute;
  width: 150px;
  height: 150px;
}

.portal:nth-child(1) { top: 20%; right: 15%; }
.portal:nth-child(2) { bottom: 30%; left: 10%; }
.portal:nth-child(3) { top: 60%; right: 40%; }

.portal-ring {
  position: absolute;
  border: 1px solid rgba(138, 43, 226, 0.4);
  border-radius: 50%;
  animation: portal-expand 4s ease-out infinite;
}

.portal-ring:nth-child(1) { width: 30px; height: 30px; top: 50%; left: 50%; transform: translate(-50%, -50%); animation-delay: 0s; }
.portal-ring:nth-child(2) { width: 60px; height: 60px; top: 50%; left: 50%; transform: translate(-50%, -50%); animation-delay: 0.8s; }
.portal-ring:nth-child(3) { width: 90px; height: 90px; top: 50%; left: 50%; transform: translate(-50%, -50%); animation-delay: 1.6s; }
.portal-ring:nth-child(4) { width: 120px; height: 120px; top: 50%; left: 50%; transform: translate(-50%, -50%); animation-delay: 2.4s; }
.portal-ring:nth-child(5) { width: 150px; height: 150px; top: 50%; left: 50%; transform: translate(-50%, -50%); animation-delay: 3.2s; }

.portal-core {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 20px;
  height: 20px;
  background: radial-gradient(circle, #ff00ff 0%, #8a2be2 50%, transparent 100%);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  animation: portal-core-pulse 2s ease-in-out infinite;
}

@keyframes portal-expand {
  0% { opacity: 1; transform: translate(-50%, -50%) scale(0.5); }
  100% { opacity: 0; transform: translate(-50%, -50%) scale(2); }
}

@keyframes portal-core-pulse {
  0%, 100% { opacity: 0.6; transform: translate(-50%, -50%) scale(1); }
  50% { opacity: 1; transform: translate(-50%, -50%) scale(1.5); }
}

/* HERO SECTION */
.hero-section {
  padding: 12rem 0 8rem;
  text-align: center;
  background: radial-gradient(ellipse at center, rgba(10, 10, 46, 0.95) 0%, rgba(22, 33, 62, 0.9) 25%, rgba(15, 52, 96, 0.85) 50%, rgba(0, 0, 0, 0.95) 100%);
  border-bottom: 1px solid rgba(135, 206, 235, 0.3);
  position: relative;
  overflow: hidden;
  min-height: 100vh;
}

.galaxy-section {
  background: radial-gradient(ellipse at center, rgba(10, 10, 46, 0.95) 0%, rgba(22, 33, 62, 0.9) 25%, rgba(15, 52, 96, 0.85) 50%, rgba(0, 0, 0, 0.95) 100%);
  color: #ffffff;
  position: relative;
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

/* PROFILE IMAGE SECTION */
.profile-image-container {
  margin-bottom: 3rem;
  position: relative;
  display: flex;
  justify-content: center;
  z-index: 10;
}

.profile-image {
  width: 200px;
  height: 200px;
  border-radius: 50%;
  object-fit: cover;
  border: 4px solid #64c8ff;
  box-shadow: 
    0 0 30px rgba(100, 200, 255, 0.5),
    0 0 60px rgba(0, 255, 136, 0.3),
    0 10px 40px rgba(0, 0, 0, 0.3);
  transition: all 0.5s ease;
  animation: profile-float 6s ease-in-out infinite;
}

.profile-image:hover {
  transform: scale(1.1);
  box-shadow: 
    0 0 50px rgba(100, 200, 255, 0.8),
    0 0 100px rgba(0, 255, 136, 0.6),
    0 20px 60px rgba(0, 0, 0, 0.4);
  border-color: #00ff88;
}

.profile-glow {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 220px;
  height: 220px;
  background: radial-gradient(circle, rgba(100, 200, 255, 0.2) 0%, transparent 70%);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  animation: profile-glow-pulse 4s ease-in-out infinite;
  z-index: -1;
}

@keyframes profile-float {
  0%, 100% { transform: translateY(0) rotate(0deg); }
  25% { transform: translateY(-10px) rotate(2deg); }
  50% { transform: translateY(0) rotate(0deg); }
  75% { transform: translateY(-5px) rotate(-2deg); }
}

@keyframes profile-glow-pulse {
  0%, 100% { 
    opacity: 0.6; 
    transform: translate(-50%, -50%) scale(1); 
  }
  50% { 
    opacity: 1; 
    transform: translate(-50%, -50%) scale(1.2); 
  }
}

/* JOURNEY IMAGE SECTION */
.journey-image-container {
  margin: 3rem auto;
  max-width: 600px;
  position: relative;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 
    0 10px 30px rgba(0, 0, 0, 0.2),
    0 0 40px rgba(100, 200, 255, 0.3);
  transition: all 0.5s ease;
}

.journey-image-container:hover {
  transform: translateY(-10px);
  box-shadow: 
    0 20px 50px rgba(0, 0, 0, 0.3),
    0 0 60px rgba(100, 200, 255, 0.5);
}

.journey-image {
  width: 100%;
  height: 400px;
  object-fit: cover;
  transition: all 0.5s ease;
}

.journey-image-container:hover .journey-image {
  transform: scale(1.05);
}

.journey-overlay {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background: linear-gradient(transparent, rgba(0, 0, 0, 0.8));
  padding: 2rem;
  transform: translateY(100%);
  transition: transform 0.5s ease;
}

.journey-image-container:hover .journey-overlay {
  transform: translateY(0);
}

.journey-caption {
  color: #ffffff;
  font-size: 1.125rem;
  font-weight: var(--font-weight-semibold);
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
}

/* VENTURES IMAGE SECTION */
.ventures-image-container {
  margin: 3rem auto;
  max-width: 700px;
  position: relative;
  border-radius: 25px;
  overflow: hidden;
  background: linear-gradient(135deg, #0a0a1a, #000000);
  box-shadow: 
    0 15px 40px rgba(0, 0, 0, 0.3),
    0 0 50px rgba(0, 255, 136, 0.3);
}

.ventures-image {
  width: 100%;
  height: 450px;
  object-fit: cover;
  transition: all 0.5s ease;
  filter: brightness(0.9) contrast(1.1);
}

.ventures-image-container:hover .ventures-image {
  transform: scale(1.03);
  filter: brightness(1.1) contrast(1.2);
}

.ventures-stats {
  position: absolute;
  top: 2rem;
  right: 2rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  background: rgba(0, 0, 0, 0.8);
  padding: 1.5rem;
  border-radius: 15px;
  border: 1px solid rgba(100, 200, 255, 0.5);
  backdrop-filter: blur(10px);
  transform: translateX(100%);
  transition: transform 0.5s ease;
}

.ventures-image-container:hover .ventures-stats {
  transform: translateX(0);
}

.ventures-stats .stat-item {
  text-align: center;
  color: #ffffff;
}

.ventures-stats .stat-number {
  display: block;
  font-size: 1.5rem;
  font-weight: var(--font-weight-bold);
  font-family: var(--font-family-mono);
  color: #64c8ff;
  margin-bottom: 0.25rem;
}

.ventures-stats .stat-label {
  font-size: 0.75rem;
  color: #cccccc;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

/* POWER QUOTE SECTION */
.quote-power-section {
  background: radial-gradient(circle at center, #000000, #0a0a1a);
  padding: 8rem 0;
  position: relative;
  overflow: hidden;
}

.power-quote-container {
  max-width: 800px;
  margin: 0 auto;
  text-align: center;
  position: relative;
  z-index: 10;
}

.quote-background-stars {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
}

.quote-background-stars .star {
  position: absolute;
  width: 2px;
  height: 2px;
  background: #64c8ff;
  border-radius: 50%;
  animation: star-twinkle 3s ease-in-out infinite;
}

.quote-background-stars .star:nth-child(odd) {
  background: #00ff88;
  animation-duration: 4s;
}

.quote-background-stars .star:nth-child(3n) {
  background: #ffffff;
  animation-duration: 2s;
}

@keyframes star-twinkle {
  0%, 100% { opacity: 0.3; transform: scale(1); }
  50% { opacity: 1; transform: scale(1.5); }
}

.power-quote {
  font-size: clamp(1.5rem, 4vw, 2.5rem);
  color: #ffffff;
  font-style: italic;
  line-height: 1.4;
  margin: 0 0 2rem;
  text-shadow: 0 0 20px rgba(100, 200, 255, 0.5);
  animation: quote-glow 6s ease-in-out infinite;
}

.quote-highlight {
  color: #64c8ff;
  font-weight: var(--font-weight-bold);
  text-shadow: 0 0 30px rgba(100, 200, 255, 0.8);
  animation: highlight-pulse 3s ease-in-out infinite;
}

.quote-author {
  color: #00ff88;
  font-size: 1.25rem;
  font-weight: var(--font-weight-semibold);
  text-shadow: 0 0 15px rgba(0, 255, 136, 0.6);
}

@keyframes quote-glow {
  0%, 100% { text-shadow: 0 0 20px rgba(100, 200, 255, 0.5); }
  50% { text-shadow: 0 0 40px rgba(100, 200, 255, 0.8); }
}

@keyframes highlight-pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.05); }
}

/* Generate random positions for stars */
.quote-background-stars .star:nth-child(1) { top: 20%; left: 10%; }
.quote-background-stars .star:nth-child(2) { top: 30%; left: 80%; }
.quote-background-stars .star:nth-child(3) { top: 60%; left: 15%; }
.quote-background-stars .star:nth-child(4) { top: 15%; left: 70%; }
.quote-background-stars .star:nth-child(5) { top: 80%; left: 25%; }
.quote-background-stars .star:nth-child(6) { top: 45%; left: 90%; }
.quote-background-stars .star:nth-child(7) { top: 70%; left: 60%; }
.quote-background-stars .star:nth-child(8) { top: 25%; left: 40%; }
.quote-background-stars .star:nth-child(9) { top: 85%; left: 75%; }
.quote-background-stars .star:nth-child(10) { top: 10%; left: 50%; }
.quote-background-stars .star:nth-child(11) { top: 55%; left: 5%; }
.quote-background-stars .star:nth-child(12) { top: 35%; left: 95%; }
.quote-background-stars .star:nth-child(13) { top: 75%; left: 35%; }
.quote-background-stars .star:nth-child(14) { top: 40%; left: 20%; }
.quote-background-stars .star:nth-child(15) { top: 90%; left: 85%; }
.quote-background-stars .star:nth-child(16) { top: 5%; left: 30%; }
.quote-background-stars .star:nth-child(17) { top: 65%; left: 65%; }
.quote-background-stars .star:nth-child(18) { top: 50%; left: 80%; }
.quote-background-stars .star:nth-child(19) { top: 20%; left: 60%; }
.quote-background-stars .star:nth-child(20) { top: 95%; left: 45%; }

/* MINDSET SECTION WHITE TITLE */
.mindset-title-white {
  color: #ffffff !important;
  text-shadow: 0 0 30px rgba(255, 255, 255, 0.8);
  animation: title-float 4s ease-in-out infinite;
}

@keyframes title-float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}

.mindset-stars-background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 1;
}

.mindset-star {
  position: absolute;
  width: 3px;
  height: 3px;
  background: #ffffff;
  border-radius: 50%;
  animation: mindset-star-dance 5s ease-in-out infinite;
}

.mindset-star:nth-child(odd) {
  background: #64c8ff;
  animation-duration: 6s;
}

.mindset-star:nth-child(3n) {
  background: #00ff88;
  animation-duration: 4s;
}

@keyframes mindset-star-dance {
  0%, 100% { 
    opacity: 0.5; 
    transform: translateY(0) rotate(0deg) scale(1); 
  }
  25% { 
    opacity: 1; 
    transform: translateY(-20px) rotate(90deg) scale(1.5); 
  }
  50% { 
    opacity: 0.8; 
    transform: translateY(-10px) rotate(180deg) scale(1.2); 
  }
  75% { 
    opacity: 1; 
    transform: translateY(-30px) rotate(270deg) scale(1.8); 
  }
}

/* Generate positions for mindset stars */
.mindset-star:nth-child(1) { top: 10%; left: 5%; }
.mindset-star:nth-child(2) { top: 25%; left: 85%; }
.mindset-star:nth-child(3) { top: 40%; left: 10%; }
.mindset-star:nth-child(4) { top: 55%; left: 90%; }
.mindset-star:nth-child(5) { top: 70%; left: 15%; }
.mindset-star:nth-child(6) { top: 15%; left: 75%; }
.mindset-star:nth-child(7) { top: 85%; left: 20%; }
.mindset-star:nth-child(8) { top: 30%; left: 60%; }
.mindset-star:nth-child(9) { top: 60%; left: 80%; }
.mindset-star:nth-child(10) { top: 80%; left: 40%; }

/* ENHANCED CRAZY ANIMATIONS */
.directive-card:hover {
  transform: translateY(-20px) perspective(1000px) rotateX(25deg) rotateY(25deg) scale(1.15) translateZ(100px);
  box-shadow: 
    0 60px 120px rgba(100, 200, 255, 0.7),
    0 40px 80px rgba(0, 255, 136, 0.6),
    0 25px 50px rgba(0, 0, 0, 0.8),
    inset 0 0 0 3px rgba(100, 200, 255, 1),
    inset 0 3px 0 rgba(255, 255, 255, 0.4);
  border-color: rgba(100, 200, 255, 1);
  background: rgba(0, 10, 30, 0.98);
  filter: brightness(1.4) contrast(1.3) saturate(1.5);
  animation: crazy-wobble 0.5s ease-in-out;
}

@keyframes crazy-wobble {
  0%, 100% { transform: translateY(-20px) perspective(1000px) rotateX(25deg) rotateY(25deg) scale(1.15) translateZ(100px); }
  25% { transform: translateY(-25px) perspective(1000px) rotateX(30deg) rotateY(20deg) scale(1.18) translateZ(120px); }
  50% { transform: translateY(-15px) perspective(1000px) rotateX(20deg) rotateY(30deg) scale(1.12) translateZ(80px); }
  75% { transform: translateY(-30px) perspective(1000px) rotateX(35deg) rotateY(15deg) scale(1.2) translateZ(140px); }
}

.constellation-card:hover {
  transform: translateY(-25px) perspective(1200px) rotateX(30deg) rotateY(30deg) scale(1.2) translateZ(120px);
  box-shadow: 
    0 70px 140px rgba(100, 200, 255, 0.8),
    0 50px 100px rgba(0, 255, 136, 0.7),
    0 30px 60px rgba(0, 0, 0, 0.9),
    inset 0 0 0 4px rgba(0, 255, 136, 1);
  animation: constellation-spin 0.8s ease-in-out;
}

@keyframes constellation-spin {
  0% { transform: translateY(-25px) perspective(1200px) rotateX(30deg) rotateY(30deg) scale(1.2) translateZ(120px); }
  50% { transform: translateY(-30px) perspective(1200px) rotateX(40deg) rotateY(40deg) scale(1.25) translateZ(150px) rotateZ(5deg); }
  100% { transform: translateY(-25px) perspective(1200px) rotateX(30deg) rotateY(30deg) scale(1.2) translateZ(120px); }
}

.mindset-card:hover {
  transform: translateY(-30px) perspective(1500px) rotateX(35deg) rotateY(35deg) scale(1.25) translateZ(150px);
  box-shadow: 
    0 80px 160px rgba(100, 200, 255, 0.9),
    0 60px 120px rgba(0, 255, 136, 0.8),
    0 40px 80px rgba(0, 0, 0, 1),
    inset 0 0 0 5px rgba(255, 255, 255, 0.8);
  animation: mindset-explosion 0.6s ease-in-out;
}

@keyframes mindset-explosion {
  0%, 100% { transform: translateY(-30px) perspective(1500px) rotateX(35deg) rotateY(35deg) scale(1.25) translateZ(150px); }
  50% { transform: translateY(-40px) perspective(1500px) rotateX(45deg) rotateY(45deg) scale(1.3) translateZ(200px) rotateZ(10deg); }
}

/* PROFILE IMAGE ENHANCEMENTS */
.profile-image:hover {
  transform: scale(1.2) rotateY(15deg) rotateX(10deg);
  box-shadow: 
    0 0 80px rgba(100, 200, 255, 1),
    0 0 160px rgba(0, 255, 136, 0.8),
    0 30px 80px rgba(0, 0, 0, 0.6);
  border-color: #00ff88;
  animation: profile-crazy-spin 1s ease-in-out;
}

@keyframes profile-crazy-spin {
  0% { transform: scale(1.2) rotateY(15deg) rotateX(10deg); }
  25% { transform: scale(1.25) rotateY(25deg) rotateX(15deg) rotateZ(5deg); }
  50% { transform: scale(1.3) rotateY(35deg) rotateX(20deg) rotateZ(-5deg); }
  75% { transform: scale(1.25) rotateY(25deg) rotateX(15deg) rotateZ(3deg); }
  100% { transform: scale(1.2) rotateY(15deg) rotateX(10deg); }
}

/* CRAZY MOVING ELEMENTS */
.floating-element {
  animation: crazy-float 8s ease-in-out infinite;
}

@keyframes crazy-float {
  0%, 100% { transform: translateY(0) translateX(0) rotate(0deg); }
  10% { transform: translateY(-15px) translateX(5px) rotate(2deg); }
  20% { transform: translateY(-10px) translateX(-3px) rotate(-1deg); }
  30% { transform: translateY(-20px) translateX(8px) rotate(3deg); }
  40% { transform: translateY(-5px) translateX(-6px) rotate(-2deg); }
  50% { transform: translateY(-25px) translateX(10px) rotate(4deg); }
  60% { transform: translateY(-8px) translateX(-8px) rotate(-3deg); }
  70% { transform: translateY(-18px) translateX(12px) rotate(5deg); }
  80% { transform: translateY(-12px) translateX(-10px) rotate(-4deg); }
  90% { transform: translateY(-22px) translateX(6px) rotate(2deg); }
}

/* NEXBOT SECTION */
.nexbot-section {
  margin: 6rem 0;
  max-width: 800px;
  margin-left: auto;
  margin-right: auto;
  position: relative;
  z-index: 5;
  animation: nexbot-hover 10s ease-in-out infinite;
}

@keyframes nexbot-hover {
  0%, 100% { transform: translateY(0) scale(1); }
  25% { transform: translateY(-10px) scale(1.02); }
  50% { transform: translateY(-5px) scale(1.01); }
  75% { transform: translateY(-15px) scale(1.03); }
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
  
  /* Mobile Image Adjustments */
  .profile-image {
    width: 150px !important;
    height: 150px !important;
  }
  
  .profile-glow {
    width: 170px !important;
    height: 170px !important;
  }
  
  .journey-image-container {
    margin: 2rem auto !important;
    max-width: 90% !important;
  }
  
  .journey-image {
    height: 250px !important;
  }
  
  .journey-overlay {
    padding: 1rem !important;
  }
  
  .journey-caption {
    font-size: 0.875rem !important;
  }
  
  .ventures-image-container {
    margin: 2rem auto !important;
    max-width: 90% !important;
  }
  
  .ventures-image {
    height: 300px !important;
  }
  
  .ventures-stats {
    position: static !important;
    transform: none !important;
    margin-top: 1rem !important;
    background: rgba(0, 0, 0, 0.9) !important;
  }
  
  .ventures-stats .stat-number {
    font-size: 1.25rem !important;
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

/* ===== WELCOME POPUP ===== */
.welcome-popup {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  z-index: 10000;
  display: flex;
  align-items: center;
  justify-content: center;
}

.popup-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: radial-gradient(circle at center, rgba(0, 0, 0, 0.95) 0%, rgba(0, 0, 0, 0.98) 100%);
  backdrop-filter: blur(10px);
}

.popup-content {
  position: relative;
  width: 90%;
  max-width: 600px;
  background: linear-gradient(135deg, #0a0a0a 0%, #1a1a1a 50%, #0a0a0a 100%);
  border: 2px solid #00ff88;
  border-radius: 20px;
  padding: 3rem;
  box-shadow: 
    0 0 100px rgba(0, 255, 136, 0.3),
    inset 0 0 50px rgba(0, 255, 136, 0.1);
  animation: popup-materialize 1s ease-out;
  overflow: hidden;
}

@keyframes popup-materialize {
  0% {
    opacity: 0;
    transform: scale(0.5) rotateY(180deg);
  }
  50% {
    transform: scale(1.1) rotateY(90deg);
  }
  100% {
    opacity: 1;
    transform: scale(1) rotateY(0deg);
  }
}

.hologram-effect {
  position: relative;
  margin-bottom: 2rem;
}

.hologram-text {
  font-family: 'Courier New', monospace;
  font-size: 1.2rem;
  color: #00ff88;
  text-align: center;
  letter-spacing: 3px;
  animation: hologram-flicker 2s ease-in-out infinite;
}

@keyframes hologram-flicker {
  0%, 100% { opacity: 1; text-shadow: 0 0 10px #00ff88; }
  50% { opacity: 0.8; text-shadow: 0 0 20px #00ff88, 0 0 30px #00ff88; }
}

.hologram-scan {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, transparent, #00ff88, transparent);
  animation: scan-line 3s linear infinite;
}

@keyframes scan-line {
  0% { transform: translateY(-10px); opacity: 0; }
  50% { opacity: 1; }
  100% { transform: translateY(50px); opacity: 0; }
}

.matrix-rain {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
  opacity: 0.1;
}

.rain-column {
  position: absolute;
  top: -50px;
  width: 20px;
  height: 100%;
  color: #00ff88;
  font-family: 'Courier New', monospace;
  font-size: 12px;
  animation: matrix-fall linear infinite;
}

.rain-column:nth-child(1) { left: 5%; animation-duration: 3s; animation-delay: 0s; }
.rain-column:nth-child(2) { left: 15%; animation-duration: 2.5s; animation-delay: 0.5s; }
.rain-column:nth-child(3) { left: 25%; animation-duration: 3.5s; animation-delay: 1s; }
.rain-column:nth-child(4) { left: 35%; animation-duration: 2s; animation-delay: 1.5s; }
.rain-column:nth-child(5) { left: 45%; animation-duration: 4s; animation-delay: 0.2s; }
.rain-column:nth-child(6) { left: 55%; animation-duration: 2.8s; animation-delay: 0.8s; }
.rain-column:nth-child(7) { left: 65%; animation-duration: 3.2s; animation-delay: 1.2s; }
.rain-column:nth-child(8) { left: 75%; animation-duration: 2.3s; animation-delay: 0.3s; }
.rain-column:nth-child(9) { left: 85%; animation-duration: 3.8s; animation-delay: 1.8s; }
.rain-column:nth-child(10) { left: 95%; animation-duration: 2.7s; animation-delay: 0.7s; }

@keyframes matrix-fall {
  0% { transform: translateY(-100%); }
  100% { transform: translateY(100vh); }
}

.welcome-message {
  position: relative;
  z-index: 2;
  text-align: center;
}

.cosmic-title {
  font-size: 3rem;
  font-weight: bold;
  margin-bottom: 1rem;
  color: #fff;
}

.glitch-effect {
  position: relative;
  display: inline-block;
  animation: glitch-shake 4s ease-in-out infinite;
}

.glitch-effect::before,
.glitch-effect::after {
  content: attr(data-text);
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.glitch-effect::before {
  color: #ff0040;
  animation: glitch-anim-1 2s infinite linear alternate-reverse;
}

.glitch-effect::after {
  color: #00ff88;
  animation: glitch-anim-2 1s infinite linear alternate-reverse;
}

@keyframes glitch-shake {
  0%, 100% { transform: translate(0); }
  20% { transform: translate(-2px, 2px); }
  40% { transform: translate(-2px, -2px); }
  60% { transform: translate(2px, 2px); }
  80% { transform: translate(2px, -2px); }
}

@keyframes glitch-anim-1 {
  0% { clip-path: inset(40% 0 61% 0); }
  20% { clip-path: inset(92% 0 1% 0); }
  40% { clip-path: inset(43% 0 1% 0); }
  60% { clip-path: inset(25% 0 58% 0); }
  80% { clip-path: inset(54% 0 7% 0); }
  100% { clip-path: inset(58% 0 43% 0); }
}

@keyframes glitch-anim-2 {
  0% { clip-path: inset(25% 0 58% 0); }
  20% { clip-path: inset(54% 0 7% 0); }
  40% { clip-path: inset(58% 0 43% 0); }
  60% { clip-path: inset(40% 0 61% 0); }
  80% { clip-path: inset(92% 0 1% 0); }
  100% { clip-path: inset(43% 0 1% 0); }
}

.subtitle {
  color: #888;
  font-size: 1.1rem;
  margin-bottom: 2rem;
  letter-spacing: 1px;
}

.tech-specs {
  text-align: left;
  margin: 2rem 0;
}

.spec-line {
  display: flex;
  justify-content: space-between;
  margin-bottom: 0.5rem;
  font-family: 'Courier New', monospace;
}

.label {
  color: #00ff88;
  font-weight: bold;
}

.value {
  color: #fff;
}

.typing-effect {
  animation: typing 2s steps(10) infinite;
}

@keyframes typing {
  0%, 50% { opacity: 1; }
  51%, 100% { opacity: 0.5; }
}

.enter-btn {
  position: relative;
  background: linear-gradient(45deg, #00ff88, #004e92);
  color: white;
  border: none;
  padding: 1rem 2rem;
  border-radius: 50px;
  font-size: 1.1rem;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease;
  overflow: hidden;
}

.enter-btn:hover {
  transform: scale(1.05);
  box-shadow: 0 0 30px rgba(0, 255, 136, 0.5);
}

.btn-glow {
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
  animation: btn-shine 3s ease-in-out infinite;
}

@keyframes btn-shine {
  0% { left: -100%; }
  50% { left: 100%; }
  100% { left: 100%; }
}

.close-btn {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: none;
  border: 2px solid #ff0040;
  color: #ff0040;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  font-size: 1.5rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.close-btn:hover {
  background: #ff0040;
  color: white;
  transform: rotate(90deg);
}

/* ===== BUSINESS TRANSFORMATION SECTION ===== */
.transformation-chaos-section {
  background: linear-gradient(135deg, #000000 0%, #1a0000 50%, #000000 100%);
  padding: 10rem 0;
  position: relative;
  overflow: hidden;
}

.transformation-container {
  position: relative;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.chaos-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
}

.lightning-bolts {
  position: absolute;
  width: 100%;
  height: 100%;
}

.lightning {
  position: absolute;
  width: 2px;
  height: 100%;
  background: linear-gradient(to bottom, transparent, #ff0040, #ffffff, #ff0040, transparent);
  animation: lightning-strike 3s ease-in-out infinite;
}

.lightning:nth-child(1) { left: 10%; animation-delay: 0s; }
.lightning:nth-child(2) { left: 30%; animation-delay: 0.5s; }
.lightning:nth-child(3) { left: 50%; animation-delay: 1s; }
.lightning:nth-child(4) { left: 70%; animation-delay: 1.5s; }
.lightning:nth-child(5) { left: 90%; animation-delay: 2s; }

@keyframes lightning-strike {
  0%, 90%, 100% { opacity: 0; transform: scaleY(0); }
  95% { opacity: 1; transform: scaleY(1); }
}

.data-explosions {
  position: absolute;
  width: 100%;
  height: 100%;
}

.explosion {
  position: absolute;
  width: 200px;
  height: 200px;
  border-radius: 50%;
}

.explosion-ring {
  position: absolute;
  width: 100%;
  height: 100%;
  border: 2px solid #ff0040;
  border-radius: 50%;
  animation: explosion-expand 4s ease-out infinite;
}

.explosion-ring:nth-child(1) { animation-delay: 0s; }
.explosion-ring:nth-child(2) { animation-delay: 0.8s; }
.explosion-ring:nth-child(3) { animation-delay: 1.6s; }
.explosion-ring:nth-child(4) { animation-delay: 2.4s; }
.explosion-ring:nth-child(5) { animation-delay: 3.2s; }

@keyframes explosion-expand {
  0% { transform: scale(0); opacity: 1; }
  100% { transform: scale(3); opacity: 0; }
}

.transformation-core {
  position: relative;
  z-index: 10;
  text-align: center;
  margin-bottom: 5rem;
}

.core-title {
  font-size: 4rem;
  font-weight: 900;
  margin-bottom: 2rem;
}

.chaos-text {
  display: block;
  background: linear-gradient(45deg, #ff0040, #ffffff, #ff0040);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  text-shadow: 0 0 30px #ff0040;
  animation: chaos-pulse 2s ease-in-out infinite;
}

@keyframes chaos-pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.1); filter: brightness(1.5); }
}

.transformation-manifesto {
  font-size: 1.5rem;
  color: #ffffff;
  margin-top: 2rem;
}

.manifesto-line {
  margin: 1rem 0;
  animation: manifesto-glow 3s ease-in-out infinite;
}

.keyword {
  color: #ff0040;
  font-weight: bold;
  text-shadow: 0 0 10px #ff0040;
}

@keyframes manifesto-glow {
  0%, 100% { opacity: 0.8; }
  50% { opacity: 1; text-shadow: 0 0 20px #ffffff; }
}

.transformation-pillars {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2rem;
  position: relative;
  z-index: 10;
}

.pillar {
  background: linear-gradient(135deg, #1a0000 0%, #330000 50%, #1a0000 100%);
  border: 2px solid #ff0040;
  border-radius: 20px;
  padding: 2rem;
  position: relative;
  overflow: hidden;
  transition: all 0.3s ease;
}

.pillar:hover {
  transform: scale(1.05) rotateY(5deg);
  box-shadow: 0 0 50px rgba(255, 0, 64, 0.5);
}

.pillar-energy {
  position: absolute;
  top: 1rem;
  right: 1rem;
  width: 60px;
  height: 60px;
}

.energy-core {
  width: 100%;
  height: 100%;
  background: radial-gradient(circle, #ff0040, #ffffff);
  border-radius: 50%;
  animation: energy-rotation 3s linear infinite;
}

@keyframes energy-rotation {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

.energy-pulse {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border: 2px solid #ff0040;
  border-radius: 50%;
  animation: energy-pulse-anim 2s ease-out infinite;
}

.energy-pulse:nth-child(2) { animation-delay: 0.7s; }
.energy-pulse:nth-child(3) { animation-delay: 1.4s; }

@keyframes energy-pulse-anim {
  0% { transform: scale(1); opacity: 1; }
  100% { transform: scale(2); opacity: 0; }
}

.pillar-content {
  position: relative;
  z-index: 2;
}

.pillar-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.pillar-title {
  font-size: 1.5rem;
  font-weight: bold;
  color: #ffffff;
  margin-bottom: 1rem;
}

.pillar-description {
  color: #cccccc;
  margin-bottom: 1rem;
  line-height: 1.6;
}

.pillar-impact {
  color: #ff0040;
  font-weight: bold;
  font-size: 0.9rem;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.pillar-chaos-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
}

.chaos-particle {
  position: absolute;
  width: 4px;
  height: 4px;
  background: #ff0040;
  border-radius: 50%;
  animation: chaos-float 5s ease-in-out infinite;
}

.chaos-particle:nth-child(odd) {
  background: #ffffff;
}

@keyframes chaos-float {
  0%, 100% { transform: translateY(0) rotate(0deg); opacity: 0.3; }
  50% { transform: translateY(-20px) rotate(180deg); opacity: 1; }
}

/* Position chaos particles randomly */
.chaos-particle:nth-child(1) { top: 10%; left: 10%; animation-delay: 0s; }
.chaos-particle:nth-child(2) { top: 20%; left: 80%; animation-delay: 0.5s; }
.chaos-particle:nth-child(3) { top: 80%; left: 20%; animation-delay: 1s; }
.chaos-particle:nth-child(4) { top: 60%; left: 70%; animation-delay: 1.5s; }
.chaos-particle:nth-child(5) { top: 30%; left: 50%; animation-delay: 2s; }

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

/* CHAOS SECTION - INSANE EFFECTS */
.chaos-section {
  background: radial-gradient(circle at 30% 70%, #ff0080, #000000 30%), 
              radial-gradient(circle at 70% 30%, #0080ff, transparent 50%),
              linear-gradient(45deg, #000000, #1a001a, #001a1a, #000000);
  padding: 10rem 0;
  position: relative;
  overflow: hidden;
  min-height: 100vh;
  perspective: 2000px;
}

.chaos-container {
  position: relative;
  width: 100%;
  height: 100%;
  transform-style: preserve-3d;
}

.chaos-background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
}

/* Chaos Grid */
.chaos-grid {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: 0.3;
}

.grid-chaos-line {
  position: absolute;
  background: linear-gradient(90deg, transparent, #64c8ff, transparent);
  height: 1px;
  width: 100%;
  animation: grid-chaos-horizontal 4s linear infinite;
  filter: blur(0.5px);
}

.grid-chaos-line.vertical {
  width: 1px;
  height: 100%;
  background: linear-gradient(0deg, transparent, #00ff88, transparent);
  animation: grid-chaos-vertical 6s linear infinite;
}

.grid-chaos-line:nth-child(odd) {
  animation-delay: calc(var(--n, 0) * 0.2s);
  background: linear-gradient(90deg, transparent, #ff0080, transparent);
}

.grid-chaos-line.vertical:nth-child(odd) {
  background: linear-gradient(0deg, transparent, #ff8000, transparent);
}

@keyframes grid-chaos-horizontal {
  0% { transform: translateY(-100vh) skewX(0deg); opacity: 0; }
  20% { opacity: 1; }
  80% { opacity: 1; }
  100% { transform: translateY(100vh) skewX(15deg); opacity: 0; }
}

@keyframes grid-chaos-vertical {
  0% { transform: translateX(-100vw) skewY(0deg); opacity: 0; }
  20% { opacity: 1; }
  80% { opacity: 1; }
  100% { transform: translateX(100vw) skewY(-15deg); opacity: 0; }
}

/* Flying Objects */
.flying-objects {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.flying-cube {
  position: absolute;
  width: 40px;
  height: 40px;
  transform-style: preserve-3d;
  animation: cube-chaos 8s linear infinite;
}

.flying-cube:nth-child(odd) {
  animation-duration: 12s;
  animation-direction: reverse;
}

.cube-face {
  position: absolute;
  width: 40px;
  height: 40px;
  background: linear-gradient(45deg, #64c8ff, #00ff88);
  border: 1px solid rgba(255, 255, 255, 0.3);
  opacity: 0.8;
}

.cube-face:nth-child(1) { transform: rotateY(0deg) translateZ(20px); }
.cube-face:nth-child(2) { transform: rotateY(90deg) translateZ(20px); }
.cube-face:nth-child(3) { transform: rotateY(180deg) translateZ(20px); }
.cube-face:nth-child(4) { transform: rotateY(-90deg) translateZ(20px); }
.cube-face:nth-child(5) { transform: rotateX(90deg) translateZ(20px); }
.cube-face:nth-child(6) { transform: rotateX(-90deg) translateZ(20px); }

@keyframes cube-chaos {
  0% { 
    transform: translate3d(-100px, 100vh, -200px) rotateX(0deg) rotateY(0deg) rotateZ(0deg); 
    opacity: 0;
  }
  10% { opacity: 1; }
  90% { opacity: 1; }
  100% { 
    transform: translate3d(100vw, -100px, 200px) rotateX(720deg) rotateY(1080deg) rotateZ(360deg); 
    opacity: 0;
  }
}

.flying-sphere {
  position: absolute;
  width: 60px;
  height: 60px;
  animation: sphere-chaos 10s ease-in-out infinite;
}

.sphere-core {
  width: 100%;
  height: 100%;
  background: radial-gradient(circle at 30% 30%, #ffffff, #64c8ff, #0080ff);
  border-radius: 50%;
  box-shadow: 0 0 30px rgba(100, 200, 255, 0.8);
  animation: sphere-pulse 2s ease-in-out infinite;
}

.sphere-ring {
  position: absolute;
  top: 50%;
  left: 50%;
  border: 2px solid #00ff88;
  border-radius: 50%;
  opacity: 0.6;
  animation: ring-spin 3s linear infinite;
}

.sphere-ring:nth-child(2) { width: 80px; height: 80px; margin: -40px 0 0 -40px; }
.sphere-ring:nth-child(3) { width: 100px; height: 100px; margin: -50px 0 0 -50px; animation-direction: reverse; }
.sphere-ring:nth-child(4) { width: 120px; height: 120px; margin: -60px 0 0 -60px; animation-duration: 4s; }

@keyframes sphere-chaos {
  0% { transform: translate3d(100vw, -50px, 0) scale(0.5); }
  25% { transform: translate3d(75vw, 25vh, 100px) scale(1.2); }
  50% { transform: translate3d(50vw, 75vh, -100px) scale(0.8); }
  75% { transform: translate3d(25vw, 25vh, 150px) scale(1.5); }
  100% { transform: translate3d(-100px, 100vh, 0) scale(0.3); }
}

@keyframes sphere-pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.3); }
}

@keyframes ring-spin {
  0% { transform: rotateX(0deg) rotateY(0deg); }
  100% { transform: rotateX(360deg) rotateY(720deg); }
}

/* Wormholes */
.wormholes {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.wormhole {
  position: absolute;
  width: 200px;
  height: 200px;
  animation: wormhole-drift 15s linear infinite;
}

.wormhole-ring {
  position: absolute;
  top: 50%;
  left: 50%;
  border: 3px solid rgba(100, 200, 255, 0.4);
  border-radius: 50%;
  animation: wormhole-spin 2s linear infinite;
}

.wormhole-ring:nth-child(1) { width: 200px; height: 200px; margin: -100px 0 0 -100px; }
.wormhole-ring:nth-child(2) { width: 180px; height: 180px; margin: -90px 0 0 -90px; animation-delay: 0.25s; }
.wormhole-ring:nth-child(3) { width: 160px; height: 160px; margin: -80px 0 0 -80px; animation-delay: 0.5s; }
.wormhole-ring:nth-child(4) { width: 140px; height: 140px; margin: -70px 0 0 -70px; animation-delay: 0.75s; }
.wormhole-ring:nth-child(5) { width: 120px; height: 120px; margin: -60px 0 0 -60px; animation-delay: 1s; }
.wormhole-ring:nth-child(6) { width: 100px; height: 100px; margin: -50px 0 0 -50px; animation-delay: 1.25s; }
.wormhole-ring:nth-child(7) { width: 80px; height: 80px; margin: -40px 0 0 -40px; animation-delay: 1.5s; }
.wormhole-ring:nth-child(8) { width: 60px; height: 60px; margin: -30px 0 0 -30px; animation-delay: 1.75s; }

.wormhole-core {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 40px;
  height: 40px;
  margin: -20px 0 0 -20px;
  background: radial-gradient(circle, #ffffff, #64c8ff, #000000);
  border-radius: 50%;
  animation: core-pulse 3s ease-in-out infinite;
  box-shadow: 0 0 50px rgba(100, 200, 255, 1);
}

@keyframes wormhole-drift {
  0% { transform: translate3d(-200px, 100vh, 0) rotateZ(0deg); }
  100% { transform: translate3d(100vw, -200px, 0) rotateZ(360deg); }
}

@keyframes wormhole-spin {
  0% { transform: rotateX(0deg) scale(1); opacity: 1; }
  50% { transform: rotateX(180deg) scale(0.5); opacity: 0.3; }
  100% { transform: rotateX(360deg) scale(1); opacity: 1; }
}

@keyframes core-pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(2); }
}

/* Energy Beams */
.energy-beams {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.energy-beam {
  position: absolute;
  width: 400px;
  height: 8px;
  animation: beam-sweep 6s linear infinite;
}

.beam-core {
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, #00ff88, #64c8ff, #00ff88, transparent);
  box-shadow: 0 0 20px rgba(0, 255, 136, 0.8);
  animation: beam-intensity 2s ease-in-out infinite;
}

.beam-particles {
  position: absolute;
  top: -10px;
  left: 0;
  width: 100%;
  height: 28px;
}

.beam-particle {
  position: absolute;
  width: 4px;
  height: 4px;
  background: #64c8ff;
  border-radius: 50%;
  animation: particle-flow 1s linear infinite;
}

@keyframes beam-sweep {
  0% { transform: translate3d(-100vw, 50vh, 0) rotateZ(45deg); }
  100% { transform: translate3d(200vw, 25vh, 0) rotateZ(45deg); }
}

@keyframes beam-intensity {
  0%, 100% { opacity: 0.6; transform: scaleY(1); }
  50% { opacity: 1; transform: scaleY(2); }
}

@keyframes particle-flow {
  0% { transform: translateX(0) scale(0); opacity: 0; }
  20% { opacity: 1; transform: scale(1); }
  80% { opacity: 1; }
  100% { transform: translateX(400px) scale(0); opacity: 0; }
}

/* Chaos Message */
.chaos-message {
  position: relative;
  z-index: 100;
  text-align: center;
  padding: 4rem 2rem;
  max-width: 800px;
  margin: 0 auto;
  top: 30vh;
}

.chaos-title {
  font-size: 4rem;
  font-weight: 900;
  line-height: 1.2;
  margin-bottom: 2rem;
  perspective: 1000px;
}

.chaos-word {
  display: inline-block;
  margin: 0 1rem;
  background: linear-gradient(45deg, #64c8ff, #00ff88, #ff0080, #64c8ff);
  background-size: 400% 400%;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: 
    chaos-gradient 3s ease-in-out infinite,
    chaos-float calc(2s + var(--word-delay, 0s)) ease-in-out infinite,
    chaos-rotate calc(4s + var(--word-delay, 0s)) linear infinite;
  text-shadow: 
    0 0 30px rgba(100, 200, 255, 0.5),
    0 0 60px rgba(0, 255, 136, 0.3);
  transform-style: preserve-3d;
}

@keyframes chaos-gradient {
  0%, 100% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
}

@keyframes chaos-float {
  0%, 100% { transform: translateY(0) translateZ(0); }
  33% { transform: translateY(-20px) translateZ(30px); }
  66% { transform: translateY(10px) translateZ(-20px); }
}

@keyframes chaos-rotate {
  0% { transform: rotateY(0deg); }
  100% { transform: rotateY(360deg); }
}

.chaos-subtitle {
  font-size: 1.5rem;
  color: rgba(255, 255, 255, 0.8);
  font-weight: 300;
  letter-spacing: 2px;
  animation: subtitle-glow 4s ease-in-out infinite;
}

@keyframes subtitle-glow {
  0%, 100% { text-shadow: 0 0 20px rgba(100, 200, 255, 0.5); }
  50% { text-shadow: 0 0 40px rgba(0, 255, 136, 0.8); }
}

/* Code Matrix */
.code-matrix {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 50;
}

.code-stream {
  position: absolute;
  font-family: 'Courier New', monospace;
  font-size: 14px;
  color: #00ff88;
  writing-mode: vertical-lr;
  animation: matrix-fall 4s linear infinite;
  opacity: 0.7;
}

.code-char {
  display: block;
  text-shadow: 0 0 5px #00ff88;
  animation: char-flicker 0.5s ease-in-out infinite;
}

@keyframes matrix-fall {
  0% { transform: translateY(-100vh); opacity: 0; }
  10% { opacity: 1; }
  90% { opacity: 1; }
  100% { transform: translateY(100vh); opacity: 0; }
}

/* Enhanced Starry Background */
.starry-background {
  position: fixed;
  width: 100%;
  height: 100%;
  background: linear-gradient(45deg, #000428, #004e92);
  overflow: hidden;
  z-index: -1;
  will-change: transform;
}

.star {
  position: absolute;
  background: white;
  border-radius: 50%;
  animation: moveStar 10s linear infinite;
  will-change: transform;
  box-shadow: 0 0 6px rgba(255, 255, 255, 0.8);
}

.floating-particle {
  position: absolute;
  background: radial-gradient(circle, #00ff88, rgba(0, 255, 136, 0.3), transparent);
  border-radius: 50%;
  animation: floatParticle 20s ease-in-out infinite;
  will-change: transform;
  box-shadow: 0 0 8px rgba(0, 255, 136, 0.6);
  transition: all 0.3s ease;
}

.nebula-cloud {
  position: absolute;
  background: radial-gradient(circle, rgba(255, 0, 150, 0.1), transparent);
  border-radius: 50%;
  animation: nebulaFloat 30s ease-in-out infinite;
  will-change: transform;
  filter: blur(2px);
}

.shooting-star {
  position: absolute;
  width: 2px;
  height: 2px;
  background: white;
  animation: shootingStar 8s linear infinite;
  will-change: transform;
}

.shooting-star::before {
  content: '';
  position: absolute;
  width: var(--trail-length, 80px);
  height: 2px;
  background: linear-gradient(to right, rgba(255, 255, 255, 0.9), rgba(100, 200, 255, 0.6), transparent);
  transform: translateX(calc(-1 * var(--trail-length, 80px)));
  border-radius: 1px;
  box-shadow: 0 0 4px rgba(255, 255, 255, 0.8);
}

@keyframes moveStar {
  from { 
    transform: translate3d(0, -10vh, 0);
    opacity: 0;
  }
  10% { opacity: 1; }
  90% { opacity: 1; }
  to { 
    transform: translate3d(0, 110vh, 0);
    opacity: 0;
  }
}

@keyframes floatParticle {
  0%, 100% { 
    transform: translate3d(0, 0, 0) scale(0.8);
    opacity: 0.6;
  }
  25% { 
    transform: translate3d(20px, -30px, 0) scale(1.2);
    opacity: 1;
  }
  50% { 
    transform: translate3d(-15px, -60px, 0) scale(0.9);
    opacity: 0.8;
  }
  75% { 
    transform: translate3d(25px, -90px, 0) scale(1.1);
    opacity: 0.9;
  }
}

@keyframes nebulaFloat {
  0%, 100% { 
    transform: translate3d(0, 0, 0) scale(1);
    opacity: 0.3;
  }
  33% { 
    transform: translate3d(50px, -20px, 0) scale(1.2);
    opacity: 0.5;
  }
  66% { 
    transform: translate3d(-30px, -40px, 0) scale(0.8);
    opacity: 0.4;
  }
}

@keyframes shootingStar {
  0% { 
    transform: translate3d(-100px, -100px, 0);
    opacity: 0;
  }
  10% { opacity: 1; }
  90% { opacity: 1; }
  100% { 
    transform: translate3d(100vw, 100vh, 0);
    opacity: 0;
  }
}

/* Shake Interval Animation */
.shake-interval {
  animation: shakeInterval 8s infinite;
}

@keyframes shakeInterval {
  0%, 70% { transform: translateX(0); }
  71% { transform: translateX(-2px); }
  72% { transform: translateX(2px); }
  73% { transform: translateX(-2px); }
  74% { transform: translateX(2px); }
  75% { transform: translateX(-1px); }
  76% { transform: translateX(1px); }
  77%, 100% { transform: translateX(0); }
}
</style> 