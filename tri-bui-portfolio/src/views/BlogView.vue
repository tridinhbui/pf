<template>
  <div class="blog-view">
    <!-- Navigation -->
    <NavBar />
    
    <!-- Hero Section -->
    <section class="blog-hero">
      <div class="container">
        <div class="hero-content">
          <!-- Welcome Robot -->
          <div class="blog-robot">
            <div class="robot-container">
              <div class="robot-head">
                <div class="robot-eye left"></div>
                <div class="robot-eye right"></div>
                <div class="robot-mouth"></div>
              </div>
              <div class="robot-body">
                <div class="robot-chest"></div>
              </div>
              <div class="robot-arms">
                <div class="robot-arm left"></div>
                <div class="robot-arm right"></div>
              </div>
              <div class="robot-speech-bubble">
                <p>Welcome to Tri's Blog!</p>
              </div>
            </div>
          </div>
          
          <h1 class="hero-title">
            <span class="title-main">Insights & Perspectives</span>
            <span class="title-sub">Where Innovation Meets Strategy</span>
          </h1>
          <p class="hero-description">
            Exploring the intersection of finance, technology, and entrepreneurship through 
            data-driven insights and strategic perspectives on building the future.
          </p>
        </div>
      </div>
    </section>

    <!-- Featured Article -->
    <section class="featured-section">
      <div class="container">
        <div class="featured-article">
          <div class="featured-content">
            <span class="featured-tag">Featured</span>
            <h2 class="featured-title">The Future of AI in Financial Services</h2>
            <p class="featured-excerpt">
              How artificial intelligence is reshaping risk assessment, portfolio optimization, 
              and customer experience in the financial sector. A deep dive into implementation 
              strategies and real-world applications.
            </p>
            <div class="featured-meta">
              <span class="meta-date">March 15, 2024</span>
              <span class="meta-read-time">8 min read</span>
              <span class="meta-category">FinTech</span>
            </div>
            <router-link to="/blog/article/1" class="read-article-btn">Read Full Article</router-link>
          </div>
          <div class="featured-image">
            <div class="image-placeholder">
              <div class="ai-visualization">
                <div class="neural-network">
                  <div class="node" v-for="n in 12" :key="n"></div>
                  <div class="connection" v-for="n in 20" :key="n"></div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Blog Categories -->
    <section class="categories-section">
      <div class="container">
        <h2 class="section-title">Explore by Category</h2>
        <div class="categories-grid">
          <div class="category-card" v-for="category in categories" :key="category.name" @click="selectCategory(category.name)">
            <div class="category-icon">{{ category.icon }}</div>
            <h3 class="category-name">{{ category.name }}</h3>
            <p class="category-description">{{ category.description }}</p>
            <span class="article-count">{{ category.count }} articles</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Recent Articles -->
    <section class="articles-section">
      <div class="container">
        <div class="section-header">
          <h2 class="section-title">Recent Articles</h2>
          <div class="filters">
            <button 
              v-for="filter in filters" 
              :key="filter"
              class="filter-btn"
              :class="{ 'active': selectedFilter === filter }"
              @click="selectedFilter = filter"
            >
              {{ filter }}
            </button>
          </div>
        </div>
        
        <div class="articles-grid">
          <article class="article-card" v-for="article in filteredArticles" :key="article.id">
            <div class="article-image">
              <div class="image-placeholder">
                <span class="article-icon">{{ article.icon }}</span>
              </div>
              <span class="article-category">{{ article.category }}</span>
            </div>
            <div class="article-content">
              <h3 class="article-title">{{ article.title }}</h3>
              <p class="article-excerpt">{{ article.excerpt }}</p>
              <div class="article-meta">
                <span class="meta-date">{{ article.date }}</span>
                <span class="meta-read-time">{{ article.readTime }}</span>
              </div>
              <router-link :to="`/blog/article/${article.id}`" class="read-more-btn">Read More</router-link>
            </div>
          </article>
        </div>
      </div>
    </section>

    <!-- Newsletter Signup -->
    <section class="newsletter-section">
      <div class="container">
        <div class="newsletter-content">
          <h2 class="newsletter-title">Stay Updated</h2>
          <p class="newsletter-description">
            Get weekly insights on finance, technology, and entrepreneurship delivered to your inbox.
          </p>
          <div class="newsletter-form">
            <input 
              type="email" 
              v-model="email" 
              placeholder="Enter your email"
              class="email-input"
            >
            <button class="subscribe-btn" @click="subscribe">Subscribe</button>
          </div>
          <p class="newsletter-note">No spam, unsubscribe anytime.</p>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'
import NavBar from '@/components/NavBar.vue'

const email = ref('')
const selectedFilter = ref('All')

const filters = ['All', 'FinTech', 'AI/ML', 'Entrepreneurship', 'Strategy']

const categories = [
  {
    name: 'FinTech Innovation',
    icon: '$',
    description: 'Exploring the latest trends in financial technology and digital banking.',
    count: 12
  },
  {
    name: 'AI & Machine Learning',
    icon: '⚡',
    description: 'Deep dives into artificial intelligence applications in business.',
    count: 8
  },
  {
    name: 'Entrepreneurship',
    icon: '▲',
    description: 'Lessons learned from building and scaling successful ventures.',
    count: 15
  },
  {
    name: 'Strategic Thinking',
    icon: '◊',
    description: 'Frameworks and methodologies for strategic decision making.',
    count: 10
  },
  {
    name: 'Market Analysis',
    icon: '■',
    description: 'Data-driven insights into market trends and opportunities.',
    count: 7
  },
  {
    name: 'Leadership',
    icon: '◆',
    description: 'Perspectives on effective leadership in the digital age.',
    count: 6
  }
]

const articles = [
  {
    id: 1,
    title: 'Building Resilient Financial Models in Uncertain Markets',
    excerpt: 'How Monte Carlo simulations and stress testing helped identify $1.5M in potential downside risk.',
    category: 'FinTech',
    date: 'March 10, 2024',
    readTime: '6 min read',
    icon: '↗'
  },
  {
    id: 2,
    title: 'The Rise of Autonomous Financial Advisors',
    excerpt: 'Exploring how AI-powered platforms are democratizing financial planning and investment advice.',
    category: 'AI/ML',
    date: 'March 5, 2024',
    readTime: '9 min read',
    icon: '⚙'
  },
  {
    id: 3,
    title: 'Scaling EdTech: Lessons from YoungPreneur Academy',
    excerpt: 'How we achieved 71% internship success rate and trained 220+ students in entrepreneurship.',
    category: 'Entrepreneurship',
    date: 'February 28, 2024',
    readTime: '7 min read',
    icon: '◉'
  },
  {
    id: 4,
    title: 'Computer Vision in Manufacturing: A Daikin Case Study',
    excerpt: 'Implementing automated quality control systems that reduced defect rates by 12%.',
    category: 'AI/ML',
    date: 'February 20, 2024',
    readTime: '5 min read',
    icon: '●'
  },
  {
    id: 5,
    title: 'Strategic Portfolio Optimization for Real Estate',
    excerpt: 'Managing $350M in assets through data-driven investment strategies and risk assessment.',
    category: 'Strategy',
    date: 'February 15, 2024',
    readTime: '8 min read',
    icon: '▣'
  },
  {
    id: 6,
    title: 'The Psychology of User Retention in FinTech',
    excerpt: 'How FinBud AI achieved 87% Day-30 retention through behavioral design principles.',
    category: 'FinTech',
    date: 'February 10, 2024',
    readTime: '6 min read',
    icon: '◎'
  }
]

const filteredArticles = computed(() => {
  if (selectedFilter.value === 'All') {
    return articles
  }
  return articles.filter(article => article.category === selectedFilter.value)
})

const selectCategory = (categoryName: string) => {
  // Map category names to filter names
  const categoryFilterMap: { [key: string]: string } = {
    'FinTech Innovation': 'FinTech',
    'AI & Machine Learning': 'AI/ML',
    'Entrepreneurship': 'Entrepreneurship',
    'Strategic Thinking': 'Strategy',
    'Market Analysis': 'Strategy',
    'Leadership': 'Strategy'
  }
  
  selectedFilter.value = categoryFilterMap[categoryName] || 'All'
}

const subscribe = () => {
  if (email.value) {
    alert('Thank you for subscribing! You will receive weekly insights in your inbox.')
    email.value = ''
  }
}
</script>

<style scoped>
.blog-view {
  min-height: 100vh;
  background: #ffffff;
  color: #000000;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

/* Hero Section */
.blog-hero {
  padding: 10rem 0 4rem;
  background: #ffffff;
  position: relative;
}

.blog-hero::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: 
    radial-gradient(ellipse at center, rgba(0, 0, 0, 0.05) 0%, transparent 70%);
}

.hero-content {
  text-align: center;
  max-width: 800px;
  margin: 0 auto;
  position: relative;
  z-index: 2;
}

/* Blog Robot */
.blog-robot {
  margin-bottom: 3rem;
  display: flex;
  justify-content: center;
}

.robot-container {
  position: relative;
  width: 120px;
  height: 150px;
  animation: robot-float 3s ease-in-out infinite;
}

.robot-head {
  width: 60px;
  height: 60px;
  background: linear-gradient(145deg, #f0f0f0, #d0d0d0);
  border: 2px solid #333;
  border-radius: 15px;
  position: relative;
  margin: 0 auto 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.robot-eye {
  width: 12px;
  height: 12px;
  background: #000;
  border-radius: 50%;
  position: absolute;
  top: 18px;
  animation: robot-blink 4s ease-in-out infinite;
}

.robot-eye.left {
  left: 12px;
}

.robot-eye.right {
  right: 12px;
}

.robot-mouth {
  width: 20px;
  height: 3px;
  background: #333;
  border-radius: 2px;
  position: absolute;
  bottom: 15px;
  left: 50%;
  transform: translateX(-50%);
  animation: robot-talk 2s ease-in-out infinite;
}

.robot-body {
  width: 50px;
  height: 70px;
  background: linear-gradient(145deg, #f5f5f5, #e0e0e0);
  border: 2px solid #333;
  border-radius: 10px;
  margin: 0 auto;
  position: relative;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.robot-chest {
  width: 20px;
  height: 20px;
  background: #333;
  border-radius: 50%;
  position: absolute;
  top: 15px;
  left: 50%;
  transform: translateX(-50%);
  animation: robot-heart 1.5s ease-in-out infinite;
}

.robot-arms {
  position: absolute;
  top: 70px;
  width: 100%;
}

.robot-arm {
  width: 8px;
  height: 40px;
  background: linear-gradient(145deg, #f0f0f0, #d0d0d0);
  border: 1px solid #333;
  border-radius: 4px;
  position: absolute;
  animation: robot-wave 3s ease-in-out infinite;
}

.robot-arm.left {
  left: 5px;
  transform-origin: top center;
}

.robot-arm.right {
  right: 5px;
  transform-origin: top center;
  animation-delay: 1.5s;
}

.robot-speech-bubble {
  position: absolute;
  top: -30px;
  left: 80px;
  background: #fff;
  border: 2px solid #333;
  border-radius: 15px;
  padding: 8px 12px;
  font-size: 12px;
  font-weight: 600;
  color: #333;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  animation: speech-float 3s ease-in-out infinite;
}

.robot-speech-bubble::before {
  content: '';
  position: absolute;
  bottom: -8px;
  left: 20px;
  width: 0;
  height: 0;
  border-left: 8px solid transparent;
  border-right: 8px solid transparent;
  border-top: 8px solid #333;
}

.robot-speech-bubble::after {
  content: '';
  position: absolute;
  bottom: -6px;
  left: 22px;
  width: 0;
  height: 0;
  border-left: 6px solid transparent;
  border-right: 6px solid transparent;
  border-top: 6px solid #fff;
}

/* Robot Animations */
@keyframes robot-float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-10px); }
}

@keyframes robot-blink {
  0%, 95%, 100% { transform: scaleY(1); }
  97% { transform: scaleY(0.1); }
}

@keyframes robot-talk {
  0%, 100% { width: 20px; }
  50% { width: 25px; }
}

@keyframes robot-heart {
  0%, 100% { background: #333; transform: translateX(-50%) scale(1); }
  50% { background: #ff4444; transform: translateX(-50%) scale(1.1); }
}

@keyframes robot-wave {
  0%, 100% { transform: rotate(0deg); }
  25% { transform: rotate(15deg); }
  75% { transform: rotate(-10deg); }
}

@keyframes speech-float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-5px); }
}

.hero-title {
  margin-bottom: 2rem;
}

.title-main {
  display: block;
  font-size: 3.5rem;
  font-weight: 800;
  background: linear-gradient(135deg, #000000, #333333);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 1rem;
}

.title-sub {
  display: block;
  font-size: 1.5rem;
  font-weight: 400;
  color: #666666;
  letter-spacing: 0.1em;
}

.hero-description {
  font-size: 1.25rem;
  line-height: 1.8;
  color: #444444;
  max-width: 600px;
  margin: 0 auto;
}

/* Featured Section */
.featured-section {
  padding: 4rem 0;
  background: #f8f9fa;
}

.featured-article {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
  background: #ffffff;
  border-radius: 20px;
  padding: 3rem;
  border: 1px solid #e9ecef;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.05);
}

.featured-tag {
  display: inline-block;
  background: linear-gradient(135deg, #ff6b6b, #ee5a24);
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 20px;
  font-size: 0.875rem;
  font-weight: 600;
  margin-bottom: 1rem;
}

.featured-title {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 1.5rem;
  line-height: 1.2;
}

.featured-excerpt {
  font-size: 1.125rem;
  line-height: 1.8;
  color: #555555;
  margin-bottom: 2rem;
}

.featured-meta {
  display: flex;
  gap: 1.5rem;
  margin-bottom: 2rem;
  font-size: 0.875rem;
  color: #777777;
}

.read-article-btn {
  display: inline-block;
  background: linear-gradient(135deg, #667eea, #764ba2);
  color: white;
  border: none;
  padding: 1rem 2rem;
  border-radius: 10px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  text-decoration: none;
}

.read-article-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 20px rgba(102, 126, 234, 0.3);
  color: white;
}

/* Featured Image */
.featured-image {
  position: relative;
}

.image-placeholder {
  width: 100%;
  height: 300px;
  background: linear-gradient(135deg, #2c3e50, #34495e);
  border-radius: 15px;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
}

.ai-visualization {
  position: relative;
  width: 100%;
  height: 100%;
}

.neural-network {
  position: absolute;
  width: 100%;
  height: 100%;
}

.node {
  position: absolute;
  width: 12px;
  height: 12px;
  background: #667eea;
  border-radius: 50%;
  box-shadow: 0 0 15px rgba(102, 126, 234, 0.6);
  animation: node-pulse 3s ease-in-out infinite;
}

.node:nth-child(1) { top: 20%; left: 20%; animation-delay: 0s; }
.node:nth-child(2) { top: 30%; left: 60%; animation-delay: 0.3s; }
.node:nth-child(3) { top: 50%; left: 30%; animation-delay: 0.6s; }
.node:nth-child(4) { top: 60%; left: 70%; animation-delay: 0.9s; }
.node:nth-child(5) { top: 80%; left: 40%; animation-delay: 1.2s; }

@keyframes node-pulse {
  0%, 100% { opacity: 0.6; transform: scale(1); }
  50% { opacity: 1; transform: scale(1.2); }
}

/* Categories Section */
.categories-section {
  padding: 4rem 0;
  background: #ffffff;
}

.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  text-align: center;
  margin-bottom: 3rem;
  color: #000000;
}

.categories-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.category-card {
  background: #f8f9fa;
  border: 1px solid #e9ecef;
  border-radius: 15px;
  padding: 2rem;
  text-align: center;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
}

.category-card:hover {
  background: #ffffff;
  transform: translateY(-5px);
  border-color: #000000;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
}

.category-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.category-name {
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 1rem;
}

.category-description {
  color: #666666;
  margin-bottom: 1rem;
  line-height: 1.6;
}

.article-count {
  color: #999999;
  font-size: 0.875rem;
}

/* Articles Section */
.articles-section {
  padding: 4rem 0;
  background: #f8f9fa;
}

.section-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 3rem;
}

.filters {
  display: flex;
  gap: 1rem;
}

.filter-btn {
  background: #f8f9fa;
  border: 1px solid #e9ecef;
  color: #666666;
  padding: 0.75rem 1.5rem;
  border-radius: 25px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.filter-btn.active,
.filter-btn:hover {
  background: #000000;
  border-color: #000000;
  color: white;
}

.articles-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
}

.article-card {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 15px;
  overflow: hidden;
  transition: all 0.3s ease;
}

.article-card:hover {
  transform: translateY(-5px);
  border-color: rgba(102, 126, 234, 0.5);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
}

.article-image {
  position: relative;
  height: 200px;
  background: linear-gradient(135deg, #667eea, #764ba2);
  display: flex;
  align-items: center;
  justify-content: center;
}

.article-icon {
  font-size: 4rem;
  filter: brightness(1.2);
}

.article-category {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: rgba(0, 0, 0, 0.7);
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 15px;
  font-size: 0.75rem;
  font-weight: 600;
}

.article-content {
  padding: 2rem;
}

.article-title {
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 1rem;
  line-height: 1.3;
}

.article-excerpt {
  color: #cccccc;
  margin-bottom: 1.5rem;
  line-height: 1.6;
}

.article-meta {
  display: flex;
  gap: 1rem;
  margin-bottom: 1.5rem;
  font-size: 0.875rem;
  color: #888888;
}

.read-more-btn {
  display: inline-block;
  background: transparent;
  border: 1px solid #000000;
  color: #000000;
  padding: 0.75rem 1.5rem;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s ease;
  text-decoration: none;
  font-weight: 500;
}

.read-more-btn:hover {
  background: #000000;
  color: white;
  border-color: #000000;
}

/* Newsletter Section */
.newsletter-section {
  padding: 4rem 0;
  background: linear-gradient(135deg, #667eea, #764ba2);
}

.newsletter-content {
  text-align: center;
  max-width: 600px;
  margin: 0 auto;
}

.newsletter-title {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 1rem;
}

.newsletter-description {
  font-size: 1.125rem;
  margin-bottom: 2rem;
  opacity: 0.9;
}

.newsletter-form {
  display: flex;
  gap: 1rem;
  margin-bottom: 1rem;
  max-width: 400px;
  margin-left: auto;
  margin-right: auto;
}

.email-input {
  flex: 1;
  padding: 1rem;
  border: none;
  border-radius: 10px;
  font-size: 1rem;
  background: rgba(255, 255, 255, 0.2);
  color: white;
  backdrop-filter: blur(10px);
}

.email-input::placeholder {
  color: rgba(255, 255, 255, 0.7);
}

.subscribe-btn {
  background: rgba(255, 255, 255, 0.2);
  border: 1px solid rgba(255, 255, 255, 0.3);
  color: white;
  padding: 1rem 2rem;
  border-radius: 10px;
  cursor: pointer;
  font-weight: 600;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
}

.subscribe-btn:hover {
  background: rgba(255, 255, 255, 0.3);
  transform: translateY(-2px);
}

.newsletter-note {
  font-size: 0.875rem;
  opacity: 0.8;
}

/* Responsive Design */
@media (max-width: 768px) {
  .container {
    padding: 0 1rem;
  }
  
  .title-main {
    font-size: 2.5rem;
  }
  
  .featured-article {
    grid-template-columns: 1fr;
    gap: 2rem;
    padding: 2rem;
  }
  
  .section-header {
    flex-direction: column;
    gap: 2rem;
    align-items: stretch;
  }
  
  .filters {
    flex-wrap: wrap;
    justify-content: center;
  }
  
  .newsletter-form {
    flex-direction: column;
  }
  
  .categories-grid {
    grid-template-columns: 1fr;
  }
  
  .articles-grid {
    grid-template-columns: 1fr;
  }
}
</style> 