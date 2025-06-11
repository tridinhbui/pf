<template>
  <div class="articles-view">
    <!-- Hero Section -->
    <section class="hero-section">
      <div class="hero-content">
        <h1 class="hero-title">
          <span class="gradient-text">Insights & Articles</span>
        </h1>
        <p class="hero-subtitle">
          Exploring the intersection of finance, technology, and entrepreneurship
        </p>
        <div class="hero-stats">
          <div class="stat">
            <span class="stat-number">{{ articles.length }}</span>
            <span class="stat-label">Articles</span>
          </div>
          <div class="stat">
            <span class="stat-number">{{ totalReads }}</span>
            <span class="stat-label">Total Reads</span>
          </div>
          <div class="stat">
            <span class="stat-number">{{ categories.length }}</span>
            <span class="stat-label">Categories</span>
          </div>
        </div>
      </div>
      <div class="hero-visual">
        <div class="floating-elements">
          <div class="element" v-for="n in 6" :key="n"></div>
        </div>
      </div>
    </section>

    <!-- Filter Section -->
    <section class="filter-section">
      <div class="filter-container">
        <div class="filter-tabs">
          <button 
            v-for="category in ['All', ...categories]" 
            :key="category"
            @click="selectedCategory = category"
            class="filter-tab"
            :class="{ 'active': selectedCategory === category }"
          >
            {{ category }}
          </button>
        </div>
        <div class="search-container">
          <svg class="search-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor">
            <circle cx="11" cy="11" r="8"></circle>
            <path d="m21 21-4.35-4.35"></path>
          </svg>
          <input 
            v-model="searchQuery"
            type="text" 
            placeholder="Search articles..."
            class="search-input"
          >
        </div>
      </div>
    </section>

    <!-- Articles Grid -->
    <section class="articles-section">
      <div class="articles-grid">
        <article 
          v-for="article in filteredArticles" 
          :key="article.id"
          class="article-card"
        >
          <div class="article-image">
            <div class="image-placeholder" :style="{ background: article.gradient }">
              <div class="article-icon">{{ article.icon }}</div>
            </div>
            <div class="article-category">{{ article.category }}</div>
          </div>
          
          <div class="article-content">
            <div class="article-meta">
              <span class="article-date">{{ formatDate(article.date) }}</span>
              <span class="article-read-time">{{ article.readTime }} min read</span>
            </div>
            
            <h3 class="article-title">{{ article.title }}</h3>
            <p class="article-excerpt">{{ article.excerpt }}</p>
            
            <div class="article-tags">
              <span 
                v-for="tag in article.tags" 
                :key="tag"
                class="article-tag"
              >
                {{ tag }}
              </span>
            </div>
            
            <div class="article-footer">
              <div class="article-stats">
                <span class="stat-item">
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor">
                    <path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"></path>
                    <circle cx="12" cy="12" r="3"></circle>
                  </svg>
                  {{ article.views }}
                </span>
                <span class="stat-item">
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor">
                    <path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"></path>
                  </svg>
                  {{ article.likes }}
                </span>
              </div>
              <button class="read-more-btn" @click="openArticle(article)">
                Read More
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor">
                  <path d="m9 18 6-6-6-6"></path>
                </svg>
              </button>
            </div>
          </div>
        </article>
      </div>
    </section>

    <!-- Article Modal -->
    <div v-if="selectedArticle" class="article-modal" @click="closeModal">
      <div class="modal-content" @click.stop>
        <button class="close-btn" @click="closeModal">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor">
            <line x1="18" y1="6" x2="6" y2="18"></line>
            <line x1="6" y1="6" x2="18" y2="18"></line>
          </svg>
        </button>
        
        <div class="modal-header">
          <div class="modal-category">{{ selectedArticle.category }}</div>
          <h2 class="modal-title">{{ selectedArticle.title }}</h2>
          <div class="modal-meta">
            <span>{{ formatDate(selectedArticle.date) }}</span>
            <span>•</span>
            <span>{{ selectedArticle.readTime }} min read</span>
            <span>•</span>
            <span>{{ selectedArticle.views }} views</span>
          </div>
        </div>
        
        <div class="modal-body">
          <div class="article-full-content" v-html="selectedArticle.content"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, onMounted } from 'vue'

interface Article {
  id: number
  title: string
  excerpt: string
  content: string
  category: string
  tags: string[]
  date: string
  readTime: number
  views: number
  likes: number
  icon: string
  gradient: string
}

const selectedCategory = ref('All')
const searchQuery = ref('')
const selectedArticle = ref<Article | null>(null)

const categories = [
  'Finance', 'Technology', 'Entrepreneurship', 'AI & ML', 'Investment'
]

const articles = ref<Article[]>([
  {
    id: 1,
    title: "The Future of AI in Financial Services: Beyond Automation",
    excerpt: "Exploring how artificial intelligence is revolutionizing financial services beyond simple automation, from risk assessment to personalized investment strategies.",
    content: `
      <p>The financial services industry stands at the precipice of a transformative era, where artificial intelligence (AI) is reshaping not just how we process transactions, but how we understand and predict market behaviors.</p>
      
      <h3>The Evolution Beyond Basic Automation</h3>
      <p>While early AI applications in finance focused on automating routine tasks, today's AI systems are capable of complex reasoning, pattern recognition, and predictive analytics that rival human expertise in specialized domains.</p>
      
      <h3>Key Applications Driving Change</h3>
      <ul>
        <li><strong>Algorithmic Trading:</strong> AI systems now execute trades in microseconds, analyzing market sentiment and news feeds in real-time.</li>
        <li><strong>Risk Assessment:</strong> Machine learning models can evaluate creditworthiness by analyzing thousands of data points beyond traditional credit scores.</li>
        <li><strong>Fraud Detection:</strong> Advanced neural networks identify suspicious patterns that would be impossible for humans to detect at scale.</li>
      </ul>
      
      <h3>The Human-AI Collaboration</h3>
      <p>The most successful implementations don't replace human expertise but augment it. Financial advisors now have AI-powered tools that can analyze client portfolios and suggest optimization strategies in real-time.</p>
      
      <h3>Looking Ahead</h3>
      <p>As we move forward, the integration of AI in finance will become more sophisticated, with quantum computing potentially unlocking new levels of computational power for financial modeling and risk analysis.</p>
    `,
    category: "Finance",
    tags: ["AI", "FinTech", "Machine Learning", "Risk Management"],
    date: "2024-12-01",
    readTime: 8,
    views: 1247,
    likes: 89,
    icon: "🤖",
    gradient: "linear-gradient(135deg, #667eea 0%, #764ba2 100%)"
  },
  {
    id: 2,
    title: "Building Scalable Microservices: Lessons from FinBud AI",
    excerpt: "Technical insights from building a financial AI platform that serves 12,000+ users with 99.9% uptime using microservices architecture.",
    content: `
      <p>When we started building FinBud AI, we knew scalability would be crucial. With financial data processing requiring both speed and reliability, we chose a microservices architecture that could grow with our user base.</p>
      
      <h3>Architecture Overview</h3>
      <p>Our system consists of 9 modular lambda functions, each responsible for specific business logic:</p>
      <ul>
        <li>User Authentication & Authorization</li>
        <li>Financial Data Aggregation</li>
        <li>AI Model Inference</li>
        <li>Real-time Analytics</li>
        <li>Notification Service</li>
      </ul>
      
      <h3>Key Technical Decisions</h3>
      <p>We implemented several critical design patterns:</p>
      <ul>
        <li><strong>Event-Driven Architecture:</strong> Services communicate through events, reducing coupling and improving resilience.</li>
        <li><strong>Circuit Breaker Pattern:</strong> Prevents cascade failures when external services are unavailable.</li>
        <li><strong>Database per Service:</strong> Each microservice owns its data, preventing database bottlenecks.</li>
      </ul>
      
      <h3>Performance Results</h3>
      <p>Our architecture delivers impressive metrics:</p>
      <ul>
        <li>99.9% uptime across all services</li>
        <li>Sub-200ms response times for 95% of requests</li>
        <li>Horizontal scaling supports 10x traffic spikes</li>
        <li>87% user retention at Day-30</li>
      </ul>
      
      <h3>Lessons Learned</h3>
      <p>The most important lesson: start with a monolith and extract services as you identify clear boundaries. Premature microservices optimization can create more problems than it solves.</p>
    `,
    category: "Technology",
    tags: ["Microservices", "AWS", "Lambda", "Architecture"],
    date: "2024-11-28",
    readTime: 12,
    views: 892,
    likes: 67,
    icon: "⚡",
    gradient: "linear-gradient(135deg, #f093fb 0%, #f5576c 100%)"
  },
  {
    id: 3,
    title: "Raising $350K in Student Scholarships: A Strategic Approach",
    excerpt: "How strategic positioning and value creation helped secure substantial funding for educational initiatives, with actionable insights for other entrepreneurs.",
    content: `
      <p>Securing $350K in scholarships wasn't just about academic achievement—it required a strategic approach to positioning, networking, and value creation that any entrepreneur can apply.</p>
      
      <h3>The Strategic Framework</h3>
      <p>I developed a three-pronged approach:</p>
      <ol>
        <li><strong>Value Demonstration:</strong> Quantified impact through measurable outcomes</li>
        <li><strong>Stakeholder Alignment:</strong> Understood what each scholarship provider valued</li>
        <li><strong>Long-term Relationship Building:</strong> Focused on mutual benefit beyond the initial award</li>
      </ol>
      
      <h3>Key Success Factors</h3>
      <p>Several factors contributed to this success:</p>
      <ul>
        <li><strong>Documentation:</strong> Maintained detailed records of all achievements and their quantifiable impact</li>
        <li><strong>Storytelling:</strong> Crafted compelling narratives that connected personal journey with organizational missions</li>
        <li><strong>Network Leverage:</strong> Utilized mentors and advisors for introductions and recommendations</li>
      </ul>
      
      <h3>The ROI Mindset</h3>
      <p>Scholarship providers are investors. They want to see returns on their investment in the form of:</p>
      <ul>
        <li>Academic excellence</li>
        <li>Leadership potential</li>
        <li>Community impact</li>
        <li>Future value creation</li>
      </ul>
      
      <h3>Actionable Takeaways</h3>
      <p>For other entrepreneurs seeking funding:</p>
      <ul>
        <li>Start building your track record early</li>
        <li>Quantify everything you can</li>
        <li>Build genuine relationships with decision-makers</li>
        <li>Always deliver more value than promised</li>
      </ul>
    `,
    category: "Entrepreneurship",
    tags: ["Fundraising", "Scholarships", "Strategy", "Networking"],
    date: "2024-11-25",
    readTime: 10,
    views: 1156,
    likes: 94,
    icon: "💰",
    gradient: "linear-gradient(135deg, #a8edea 0%, #fed6e3 100%)"
  },
  {
    id: 4,
    title: "Machine Learning in Risk Management: Real-World Applications",
    excerpt: "Practical implementation of ML models for risk assessment in financial portfolios, with case studies from managing $350M in real estate assets.",
    content: `
      <p>Managing $350M in real estate assets requires sophisticated risk management. Here's how machine learning transforms traditional risk assessment approaches.</p>
      
      <h3>Traditional vs. ML-Enhanced Risk Management</h3>
      <p>Traditional risk models rely on historical data and static parameters. ML models adapt to changing market conditions and identify non-obvious risk factors.</p>
      
      <h3>Implementation Framework</h3>
      <p>Our risk management system incorporates:</p>
      <ul>
        <li><strong>Predictive Modeling:</strong> XGBoost algorithms for default probability prediction</li>
        <li><strong>Anomaly Detection:</strong> Isolation forests for identifying unusual market behavior</li>
        <li><strong>Scenario Analysis:</strong> Monte Carlo simulations powered by neural networks</li>
      </ul>
      
      <h3>Key Metrics and Results</h3>
      <p>The ML-enhanced approach delivered:</p>
      <ul>
        <li>20% reduction in operational risk</li>
        <li>$1.5M downside risk mitigation</li>
        <li>Improved Sharpe ratio from 2.1 to 3.1</li>
        <li>Earlier warning signals for market volatility</li>
      </ul>
      
      <h3>Practical Implementation Tips</h3>
      <p>Key learnings from implementation:</p>
      <ul>
        <li>Start with simple models and iterate</li>
        <li>Ensure model interpretability for regulatory compliance</li>
        <li>Implement robust backtesting frameworks</li>
        <li>Maintain human oversight for model decisions</li>
      </ul>
      
      <h3>Future Directions</h3>
      <p>Next-generation risk management will incorporate alternative data sources, real-time sentiment analysis, and quantum computing for portfolio optimization.</p>
    `,
    category: "AI & ML",
    tags: ["Machine Learning", "Risk Management", "Real Estate", "Portfolio"],
    date: "2024-11-22",
    readTime: 9,
    views: 743,
    likes: 52,
    icon: "📊",
    gradient: "linear-gradient(135deg, #84fab0 0%, #8fd3f4 100%)"
  },
  {
    id: 5,
    title: "From Idea to 12K Users: Building FinBud AI",
    excerpt: "The complete journey of building a financial AI platform that achieved 87% Day-30 retention and 3.7 daily sessions per user.",
    content: `
      <p>Building FinBud AI from concept to 12,000 beta users taught me invaluable lessons about product development, user acquisition, and scaling technical infrastructure.</p>
      
      <h3>The Genesis</h3>
      <p>The idea emerged from a simple observation: most financial advice is either too generic or too expensive for young professionals. We set out to democratize personalized financial guidance through AI.</p>
      
      <h3>Product Development Strategy</h3>
      <p>We followed a lean startup methodology:</p>
      <ol>
        <li><strong>MVP Development:</strong> Built core functionality with minimal features</li>
        <li><strong>User Feedback Loop:</strong> Weekly interviews with beta users</li>
        <li><strong>Iterative Improvement:</strong> Bi-weekly releases based on user data</li>
        <li><strong>Scale Preparation:</strong> Planned infrastructure for 10x growth</li>
      </ol>
      
      <h3>Key Product Features</h3>
      <p>Our core features focused on user value:</p>
      <ul>
        <li>AI-powered budget optimization</li>
        <li>Personalized investment recommendations</li>
        <li>Real-time spending insights</li>
        <li>Goal-based financial planning</li>
      </ul>
      
      <h3>Growth and Retention Metrics</h3>
      <p>Our success metrics exceeded expectations:</p>
      <ul>
        <li>12,000 beta users acquired in 6 months</li>
        <li>87% Day-30 retention rate</li>
        <li>3.7 average daily sessions per user</li>
        <li>4.6/5 average app store rating</li>
      </ul>
      
      <h3>Technical Challenges and Solutions</h3>
      <p>Scaling to thousands of users presented unique challenges:</p>
      <ul>
        <li><strong>Data Processing:</strong> Implemented real-time data pipelines for financial information</li>
        <li><strong>AI Model Serving:</strong> Optimized inference times to under 200ms</li>
        <li><strong>Security:</strong> Implemented bank-level encryption for sensitive financial data</li>
      </ul>
      
      <h3>Lessons for Future Entrepreneurs</h3>
      <p>Key takeaways from the journey:</p>
      <ul>
        <li>User feedback is more valuable than feature complexity</li>
        <li>Technical scalability must be planned from day one</li>
        <li>Retention is more important than acquisition</li>
        <li>Team culture determines product quality</li>
      </ul>
    `,
    category: "Entrepreneurship",
    tags: ["Startup", "Product Development", "FinTech", "User Growth"],
    date: "2024-11-20",
    readTime: 11,
    views: 1834,
    likes: 127,
    icon: "🚀",
    gradient: "linear-gradient(135deg, #fa709a 0%, #fee140 100%)"
  },
  {
    id: 6,
    title: "Portfolio Optimization with Modern Portfolio Theory and AI",
    excerpt: "Enhancing traditional MPT with machine learning for better risk-adjusted returns in volatile markets.",
    content: `
      <p>Modern Portfolio Theory (MPT) has been the foundation of portfolio construction for decades. However, in today's volatile markets, AI enhancement can significantly improve risk-adjusted returns.</p>
      
      <h3>Traditional MPT Limitations</h3>
      <p>Classical MPT assumes:</p>
      <ul>
        <li>Normal distribution of returns</li>
        <li>Static correlation between assets</li>
        <li>Linear relationships between risk and return</li>
        <li>Efficient market hypothesis</li>
      </ul>
      
      <h3>AI-Enhanced Approach</h3>
      <p>Our enhanced framework addresses these limitations:</p>
      <ul>
        <li><strong>Dynamic Correlation Modeling:</strong> LSTM networks predict changing asset correlations</li>
        <li><strong>Non-Linear Risk Modeling:</strong> Neural networks capture complex risk relationships</li>
        <li><strong>Alternative Data Integration:</strong> Sentiment analysis and macroeconomic indicators</li>
        <li><strong>Real-Time Rebalancing:</strong> Automated portfolio adjustments based on market conditions</li>
      </ul>
      
      <h3>Implementation Results</h3>
      <p>Comparing traditional vs. AI-enhanced portfolios:</p>
      <ul>
        <li>15% improvement in Sharpe ratio</li>
        <li>25% reduction in maximum drawdown</li>
        <li>Higher consistency of returns across market cycles</li>
        <li>Better downside protection during market stress</li>
      </ul>
      
      <h3>Technical Implementation</h3>
      <p>Key components of our system:</p>
      <ul>
        <li>Python-based optimization engine</li>
        <li>Real-time data feeds from multiple sources</li>
        <li>Monte Carlo simulation for scenario analysis</li>
        <li>Backtesting framework with walk-forward analysis</li>
      </ul>
      
      <h3>Future Developments</h3>
      <p>Next-generation portfolio optimization will incorporate:</p>
      <ul>
        <li>Quantum computing for complex optimization</li>
        <li>ESG factors in risk-return calculations</li>
        <li>Behavioral finance insights</li>
        <li>Real-time regulatory compliance monitoring</li>
      </ul>
    `,
    category: "Investment",
    tags: ["Portfolio Theory", "AI", "Optimization", "Quantitative Finance"],
    date: "2024-11-18",
    readTime: 8,
    views: 567,
    likes: 41,
    icon: "📈",
    gradient: "linear-gradient(135deg, #667eea 0%, #764ba2 100%)"
  }
])

const totalReads = computed(() => {
  return articles.value.reduce((sum, article) => sum + article.views, 0)
})

const filteredArticles = computed(() => {
  let filtered = articles.value

  // Filter by category
  if (selectedCategory.value !== 'All') {
    filtered = filtered.filter(article => article.category === selectedCategory.value)
  }

  // Filter by search query
  if (searchQuery.value) {
    const query = searchQuery.value.toLowerCase()
    filtered = filtered.filter(article => 
      article.title.toLowerCase().includes(query) ||
      article.excerpt.toLowerCase().includes(query) ||
      article.tags.some(tag => tag.toLowerCase().includes(query))
    )
  }

  return filtered
})

const formatDate = (dateString: string) => {
  const date = new Date(dateString)
  return date.toLocaleDateString('en-US', { 
    year: 'numeric', 
    month: 'long', 
    day: 'numeric' 
  })
}

const openArticle = (article: Article) => {
  selectedArticle.value = article
  document.body.style.overflow = 'hidden'
}

const closeModal = () => {
  selectedArticle.value = null
  document.body.style.overflow = 'auto'
}

onMounted(() => {
  // Add any initialization logic here
})
</script>

<style scoped>
.articles-view {
  min-height: 100vh;
  background: linear-gradient(135deg, #0a0a0a 0%, #1a1a1a 100%);
  color: #ffffff;
  padding-top: 100px;
}

/* Hero Section */
.hero-section {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  max-width: 1400px;
  margin: 0 auto;
  padding: 4rem 2rem;
  align-items: center;
}

.hero-title {
  font-size: 3.5rem;
  font-weight: 700;
  line-height: 1.1;
  margin-bottom: 1.5rem;
}

.gradient-text {
  background: linear-gradient(135deg, #ffffff 0%, #cccccc 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-subtitle {
  font-size: 1.25rem;
  color: rgba(255, 255, 255, 0.7);
  margin-bottom: 3rem;
  line-height: 1.6;
}

.hero-stats {
  display: flex;
  gap: 3rem;
}

.stat {
  text-align: center;
}

.stat-number {
  display: block;
  font-size: 2.5rem;
  font-weight: 700;
  color: #ffffff;
  line-height: 1;
}

.stat-label {
  font-size: 0.875rem;
  color: rgba(255, 255, 255, 0.6);
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.hero-visual {
  position: relative;
  height: 400px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.floating-elements {
  position: relative;
  width: 100%;
  height: 100%;
}

.element {
  position: absolute;
  width: 20px;
  height: 20px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 50%;
  animation: float 6s ease-in-out infinite;
}

.element:nth-child(1) { top: 10%; left: 20%; animation-delay: 0s; }
.element:nth-child(2) { top: 30%; right: 15%; animation-delay: 1s; }
.element:nth-child(3) { bottom: 40%; left: 30%; animation-delay: 2s; }
.element:nth-child(4) { top: 60%; right: 30%; animation-delay: 3s; }
.element:nth-child(5) { bottom: 20%; right: 20%; animation-delay: 4s; }
.element:nth-child(6) { top: 20%; left: 50%; animation-delay: 5s; }

/* Filter Section */
.filter-section {
  background: rgba(255, 255, 255, 0.02);
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  padding: 2rem 0;
}

.filter-container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 2rem;
}

.filter-tabs {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}

.filter-tab {
  padding: 0.75rem 1.5rem;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 25px;
  color: rgba(255, 255, 255, 0.7);
  font-size: 0.875rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.filter-tab:hover,
.filter-tab.active {
  background: rgba(255, 255, 255, 0.1);
  border-color: rgba(255, 255, 255, 0.3);
  color: #ffffff;
}

.search-container {
  position: relative;
  display: flex;
  align-items: center;
}

.search-icon {
  position: absolute;
  left: 1rem;
  width: 20px;
  height: 20px;
  color: rgba(255, 255, 255, 0.5);
  z-index: 1;
}

.search-input {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 25px;
  padding: 0.75rem 1rem 0.75rem 3rem;
  color: #ffffff;
  font-size: 0.875rem;
  width: 300px;
  transition: all 0.3s ease;
}

.search-input:focus {
  outline: none;
  border-color: rgba(255, 255, 255, 0.3);
  background: rgba(255, 255, 255, 0.08);
}

.search-input::placeholder {
  color: rgba(255, 255, 255, 0.5);
}

/* Articles Section */
.articles-section {
  max-width: 1400px;
  margin: 0 auto;
  padding: 4rem 2rem;
}

.articles-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
  gap: 2rem;
}

.article-card {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 20px;
  overflow: hidden;
  cursor: pointer;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
}

.article-card:hover {
  transform: translateY(-5px);
  border-color: rgba(255, 255, 255, 0.2);
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.3);
}

.article-image {
  position: relative;
  height: 200px;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.image-placeholder {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
}

.article-icon {
  font-size: 3rem;
  filter: drop-shadow(0 4px 8px rgba(0, 0, 0, 0.3));
}

.article-category {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: rgba(0, 0, 0, 0.7);
  color: #ffffff;
  padding: 0.5rem 1rem;
  border-radius: 15px;
  font-size: 0.75rem;
  font-weight: 600;
  backdrop-filter: blur(10px);
}

.article-content {
  padding: 1.5rem;
}

.article-meta {
  display: flex;
  gap: 1rem;
  font-size: 0.75rem;
  color: rgba(255, 255, 255, 0.6);
  margin-bottom: 1rem;
}

.article-title {
  font-size: 1.25rem;
  font-weight: 600;
  line-height: 1.3;
  margin-bottom: 1rem;
  color: #ffffff;
}

.article-excerpt {
  color: rgba(255, 255, 255, 0.7);
  line-height: 1.5;
  margin-bottom: 1.5rem;
  font-size: 0.875rem;
}

.article-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
}

.article-tag {
  background: rgba(255, 255, 255, 0.1);
  color: rgba(255, 255, 255, 0.8);
  padding: 0.25rem 0.75rem;
  border-radius: 12px;
  font-size: 0.75rem;
  font-weight: 500;
}

.article-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.article-stats {
  display: flex;
  gap: 1rem;
}

.stat-item {
  display: flex;
  align-items: center;
  gap: 0.25rem;
  font-size: 0.75rem;
  color: rgba(255, 255, 255, 0.6);
}

.stat-item svg {
  width: 14px;
  height: 14px;
}

.read-more-btn {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 20px;
  padding: 0.5rem 1rem;
  color: #ffffff;
  font-size: 0.75rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.read-more-btn:hover {
  background: rgba(255, 255, 255, 0.15);
  border-color: rgba(255, 255, 255, 0.3);
}

.read-more-btn svg {
  width: 14px;
  height: 14px;
}

/* Article Modal */
.article-modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.9);
  backdrop-filter: blur(10px);
  z-index: 1000;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
}

.modal-content {
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.1) 0%, rgba(255, 255, 255, 0.05) 100%);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 20px;
  max-width: 800px;
  max-height: 90vh;
  overflow-y: auto;
  position: relative;
  backdrop-filter: blur(20px);
}

.close-btn {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 50%;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.3s ease;
  z-index: 1;
}

.close-btn:hover {
  background: rgba(255, 255, 255, 0.2);
}

.close-btn svg {
  width: 20px;
  height: 20px;
  color: #ffffff;
}

.modal-header {
  padding: 2rem 2rem 1rem;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.modal-category {
  display: inline-block;
  background: rgba(255, 255, 255, 0.1);
  color: #ffffff;
  padding: 0.5rem 1rem;
  border-radius: 15px;
  font-size: 0.75rem;
  font-weight: 600;
  margin-bottom: 1rem;
}

.modal-title {
  font-size: 2rem;
  font-weight: 700;
  line-height: 1.2;
  margin-bottom: 1rem;
  color: #ffffff;
}

.modal-meta {
  font-size: 0.875rem;
  color: rgba(255, 255, 255, 0.6);
  display: flex;
  gap: 0.5rem;
  align-items: center;
}

.modal-body {
  padding: 2rem;
}

.article-full-content {
  color: rgba(255, 255, 255, 0.9);
  line-height: 1.7;
}

.article-full-content h3 {
  color: #ffffff;
  font-size: 1.25rem;
  font-weight: 600;
  margin: 2rem 0 1rem;
}

.article-full-content p {
  margin-bottom: 1.5rem;
}

.article-full-content ul,
.article-full-content ol {
  margin-bottom: 1.5rem;
  padding-left: 1.5rem;
}

.article-full-content li {
  margin-bottom: 0.5rem;
}

.article-full-content strong {
  color: #ffffff;
  font-weight: 600;
}

/* Animations */
@keyframes float {
  0%, 100% {
    transform: translateY(0px) rotate(0deg);
    opacity: 0.3;
  }
  50% {
    transform: translateY(-20px) rotate(180deg);
    opacity: 0.7;
  }
}

/* Responsive Design */
@media (max-width: 1200px) {
  .hero-section {
    grid-template-columns: 1fr;
    text-align: center;
  }
  
  .hero-stats {
    justify-content: center;
  }
}

@media (max-width: 768px) {
  .hero-title {
    font-size: 2.5rem;
  }
  
  .filter-container {
    flex-direction: column;
    gap: 1rem;
  }
  
  .search-input {
    width: 100%;
  }
  
  .articles-grid {
    grid-template-columns: 1fr;
  }
  
  .modal-content {
    margin: 1rem;
    max-height: calc(100vh - 2rem);
  }
  
  .modal-title {
    font-size: 1.5rem;
  }
}
</style> 