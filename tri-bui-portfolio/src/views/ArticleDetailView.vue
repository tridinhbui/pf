<template>
  <div class="article-detail">
    <!-- Article Hero -->
    <section class="article-hero">
      <div class="container">
        <div class="hero-content">
          <div class="article-meta">
            <span class="article-category" :class="`category-${article?.category?.toLowerCase()}`">
              {{ article?.category }}
            </span>
            <span class="article-date">{{ article?.date }}</span>
            <span class="read-time">{{ article?.readTime }}</span>
          </div>
          <h1 class="article-title">{{ article?.title }}</h1>
          <p class="article-excerpt">{{ article?.excerpt }}</p>
          
          <!-- Author Info -->
          <div class="author-info">
            <div class="author-avatar">
              <div class="avatar-placeholder">TB</div>
            </div>
            <div class="author-details">
              <h3 class="author-name">Tri Bui</h3>
              <p class="author-title">Co-Founder at NextGen Investor • Finance Analyst at Smithfield</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Article Content -->
    <section class="article-content">
      <div class="container">
        <div class="content-wrapper">
          <div class="article-body">
            <div v-if="article" v-html="article.content"></div>
            <div v-else class="loading-state">
              <div class="loading-spinner"></div>
              <p>Loading article...</p>
            </div>
          </div>
          
          <!-- Article Sidebar -->
          <aside class="article-sidebar">
            <div class="sidebar-content">
              <!-- Table of Contents -->
              <div class="toc-widget">
                <h3>Table of Contents</h3>
                <ul class="toc-list">
                  <li><a href="#introduction">Introduction</a></li>
                  <li><a href="#key-insights">Key Insights</a></li>
                  <li><a href="#practical-applications">Practical Applications</a></li>
                  <li><a href="#case-studies">Case Studies</a></li>
                  <li><a href="#conclusion">Conclusion</a></li>
                </ul>
              </div>
              
              <!-- Share Widget -->
              <div class="share-widget">
                <h3>Share This Article</h3>
                <div class="share-buttons">
                  <button class="share-btn twitter" @click="shareArticle('twitter')">
                    <span class="share-icon">🐦</span>
                    Twitter
                  </button>
                  <button class="share-btn linkedin" @click="shareArticle('linkedin')">
                    <span class="share-icon">💼</span>
                    LinkedIn
                  </button>
                  <button class="share-btn copy" @click="copyArticleLink">
                    <span class="share-icon">🔗</span>
                    Copy Link
                  </button>
                </div>
              </div>

              <!-- Related Articles -->
              <div class="related-widget">
                <h3>Related Articles</h3>
                <div class="related-articles">
                  <div v-for="related in relatedArticles" :key="related.id" class="related-item">
                    <router-link :to="`/blog/article/${related.id}`" class="related-link">
                      <div class="related-icon">{{ related.icon }}</div>
                      <div class="related-content">
                        <h4 class="related-title">{{ related.title }}</h4>
                        <p class="related-category">{{ related.category }}</p>
                      </div>
                    </router-link>
                  </div>
                </div>
              </div>
            </div>
          </aside>
        </div>
      </div>
    </section>

    <!-- Newsletter CTA -->
    <section class="newsletter-cta">
      <div class="container">
        <div class="cta-content">
          <h2>Stay Updated with Financial Insights</h2>
          <p>Get weekly insights on finance, technology, and entrepreneurship delivered to your inbox.</p>
          <div class="newsletter-form">
            <input 
              type="email" 
              v-model="email" 
              placeholder="Enter your email"
              class="email-input"
            >
            <button class="subscribe-btn" @click="subscribe">Subscribe</button>
          </div>
        </div>
      </div>
    </section>

    <!-- Navigation -->
    <section class="article-navigation">
      <div class="container">
        <div class="nav-content">
          <router-link to="/blog" class="back-to-blog">
            <span class="nav-icon">←</span>
            Back to Blog
          </router-link>
          <div class="article-nav-buttons">
            <button v-if="previousArticle" @click="navigateToArticle(previousArticle.id)" class="nav-btn prev">
              <span class="nav-label">Previous</span>
              <span class="nav-title">{{ previousArticle.title }}</span>
            </button>
            <button v-if="nextArticle" @click="navigateToArticle(nextArticle.id)" class="nav-btn next">
              <span class="nav-label">Next</span>
              <span class="nav-title">{{ nextArticle.title }}</span>
            </button>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, onMounted } from 'vue'
import { useRoute, useRouter } from 'vue-router'

const route = useRoute()
const router = useRouter()
const email = ref('')

// Mock article data - in real app, this would come from API or CMS
const articles = [
  {
    id: 1,
    title: 'Building Resilient Financial Models in Uncertain Markets',
    excerpt: 'How Monte Carlo simulations and stress testing helped identify $1.5M in potential downside risk.',
    category: 'FinTech',
    date: 'March 10, 2024',
    readTime: '6 min read',
    icon: '↗',
    content: `
      <h2 id="introduction">Introduction</h2>
      <p>In today's volatile financial landscape, building resilient financial models has become more critical than ever. When I was working on portfolio optimization at Smithfield Foods, I discovered that traditional models often failed to capture the full spectrum of potential risks.</p>
      
      <h2 id="key-insights">Key Insights from Monte Carlo Simulations</h2>
      <p>Monte Carlo simulations provide a powerful tool for stress-testing financial models. By running thousands of scenarios, we can identify potential downside risks that traditional sensitivity analysis might miss.</p>
      <p>Here's what I learned during my implementation:</p>
      <ul>
        <li><strong>Scenario Diversity:</strong> The more diverse your scenarios, the better your risk assessment</li>
        <li><strong>Correlation Modeling:</strong> Understanding how different variables correlate during stress periods</li>
        <li><strong>Tail Risk Analysis:</strong> Focusing on the extreme scenarios that could cause significant losses</li>
      </ul>
      
      <h2 id="practical-applications">Practical Applications</h2>
      <p>During my time at Smithfield, I implemented a Monte Carlo framework that helped identify $1.5M in potential downside risk across our portfolio. The key was not just running the simulations, but interpreting the results in the context of our business strategy.</p>
      
      <h2 id="case-studies">Case Studies</h2>
      <p>One particularly interesting case involved our agricultural commodity exposure. Traditional models suggested minimal risk, but Monte Carlo simulations revealed significant tail risks during extreme weather events.</p>
      
      <h2 id="conclusion">Conclusion</h2>
      <p>Building resilient financial models requires more than just mathematical sophistication—it requires understanding the real-world dynamics that drive financial markets. Monte Carlo simulations, when properly implemented, provide invaluable insights for risk management.</p>
    `
  },
  {
    id: 2,
    title: 'The Rise of Autonomous Financial Advisors',
    excerpt: 'Exploring how AI-powered platforms are democratizing financial planning and investment advice.',
    category: 'AI/ML',
    date: 'March 5, 2024',
    readTime: '9 min read',
    icon: '⚙',
    content: `
      <h2 id="introduction">Introduction</h2>
      <p>The financial advisory industry is undergoing a revolutionary transformation. AI-powered platforms are not just supplementing human advisors—they're democratizing access to sophisticated financial planning.</p>
      
      <h2 id="key-insights">The Technology Behind AI Advisors</h2>
      <p>Modern AI financial advisors leverage several key technologies:</p>
      <ul>
        <li><strong>Natural Language Processing:</strong> Understanding client queries and preferences</li>
        <li><strong>Machine Learning Models:</strong> Continuous learning from market data and client outcomes</li>
        <li><strong>Portfolio Optimization Algorithms:</strong> Real-time rebalancing based on market conditions</li>
      </ul>
      
      <p>At FinBud AI, we've implemented these technologies to serve over 12,000 users, with a focus on making financial advice accessible to Gen Z.</p>
      
      <h2 id="practical-applications">Real-World Implementation</h2>
      <p>Our platform uses advanced NLP to understand user financial goals and time-series forecasting to provide personalized investment recommendations. The result? 87% Day-30 retention rate and measurable improvement in users' financial outcomes.</p>
      
      <h2 id="conclusion">The Future of Financial Advisory</h2>
      <p>Autonomous financial advisors aren't replacing human advisors—they're expanding the market by serving clients who were previously underserved. This democratization of financial advice is creating new opportunities for both advisors and investors.</p>
    `
  },
  {
    id: 3,
    title: 'Scaling EdTech: Lessons from YoungPreneur Academy',
    excerpt: 'How we achieved 71% internship success rate and trained 220+ students in entrepreneurship.',
    category: 'Entrepreneurship',
    date: 'February 28, 2024',
    readTime: '7 min read',
    icon: '◉',
    content: `
      <h2 id="introduction">Introduction</h2>
      <p>Building an educational platform that truly impacts students' lives goes beyond just creating content. At YoungPreneur Academy, we discovered that the key to success lies in combining engaging education with real-world opportunities.</p>
      
      <h2 id="key-insights">The Challenge of Youth Entrepreneurship Education</h2>
      <p>When we started YoungPreneur Academy, we identified several key challenges in traditional entrepreneurship education:</p>
      <ul>
        <li><strong>Lack of Practical Experience:</strong> Most programs focus on theory without hands-on application</li>
        <li><strong>Limited Industry Connections:</strong> Students often lack access to real business networks</li>
        <li><strong>Generic Curriculum:</strong> One-size-fits-all approaches don't cater to individual interests</li>
      </ul>
      
      <h2 id="practical-applications">Our Solution: Immersive Learning</h2>
      <p>We developed a curriculum that combines intensive workshops, mentorship programs, and real internship placements. By partnering with 50+ companies, we created pathways for students to apply their learning immediately.</p>
      
      <h2 id="case-studies">Success Metrics</h2>
      <p>After two years of operation, our results speak for themselves:</p>
      <ul>
        <li>220+ students trained across multiple cohorts</li>
        <li>71% internship success rate within 6 months of completion</li>
        <li>15+ student-founded startups launched</li>
        <li>Average 23% increase in business knowledge scores</li>
      </ul>
      
      <h2 id="conclusion">Lessons Learned</h2>
      <p>Scaling an EdTech platform requires more than just great content—it requires building an ecosystem of support, mentorship, and real opportunities. The investment in building these relationships pays dividends in student outcomes.</p>
    `
  },
  {
    id: 4,
    title: 'Computer Vision in Manufacturing: A Daikin Case Study',
    excerpt: 'Implementing automated quality control systems that reduced defect rates by 12%.',
    category: 'AI/ML',
    date: 'February 20, 2024',
    readTime: '5 min read',
    icon: '●',
    content: `
      <h2 id="introduction">Introduction</h2>
      <p>During my internship at Daikin, I had the opportunity to implement computer vision solutions for automated quality control in their HVAC manufacturing process. This project demonstrated how AI can significantly improve manufacturing efficiency and quality.</p>
      
      <h2 id="key-insights">The Problem</h2>
      <p>Traditional quality control in manufacturing relies heavily on human inspection, which can be:</p>
      <ul>
        <li><strong>Inconsistent:</strong> Human inspectors can miss defects due to fatigue or distraction</li>
        <li><strong>Slow:</strong> Manual inspection creates bottlenecks in the production line</li>
        <li><strong>Subjective:</strong> Different inspectors may have varying standards</li>
      </ul>
      
      <h2 id="practical-applications">Implementation</h2>
      <p>We developed a computer vision system using convolutional neural networks to identify defects in real-time during the manufacturing process. The system was trained on thousands of images of both defective and non-defective products.</p>
      
      <h2 id="case-studies">Results</h2>
      <p>The implementation yielded impressive results:</p>
      <ul>
        <li>12% reduction in defect rates reaching customers</li>
        <li>35% faster inspection times</li>
        <li>99.2% accuracy in defect detection</li>
        <li>ROI achieved within 8 months of deployment</li>
      </ul>
      
      <h2 id="conclusion">Key Takeaways</h2>
      <p>Computer vision in manufacturing isn't just about replacing human workers—it's about augmenting human capabilities and creating more consistent, reliable quality control processes. The key to success is proper training data and continuous model refinement.</p>
    `
  },
  {
    id: 5,
    title: 'Strategic Portfolio Optimization for Real Estate',
    excerpt: 'Managing $350M in assets through data-driven investment strategies and risk assessment.',
    category: 'Strategy',
    date: 'February 15, 2024',
    readTime: '8 min read',
    icon: '▣',
    content: `
      <h2 id="introduction">Introduction</h2>
      <p>Real estate portfolio optimization requires a delicate balance between risk and return, liquidity and growth. When managing $350M in real estate assets, every decision must be backed by data and strategic thinking.</p>
      
      <h2 id="key-insights">Portfolio Theory in Real Estate</h2>
      <p>Traditional portfolio theory applies to real estate, but with unique considerations:</p>
      <ul>
        <li><strong>Illiquidity Premium:</strong> Real estate investments require longer holding periods</li>
        <li><strong>Market Segmentation:</strong> Different property types respond differently to economic cycles</li>
        <li><strong>Location Risk:</strong> Geographic diversification is crucial for risk management</li>
      </ul>
      
      <h2 id="practical-applications">Our Strategy</h2>
      <p>We developed a quantitative framework that considers multiple factors:</p>
      <ul>
        <li>Market fundamentals and demographic trends</li>
        <li>Cash flow projections and NPV analysis</li>
        <li>Risk-adjusted returns using Monte Carlo simulations</li>
        <li>Correlation analysis across different asset classes</li>
      </ul>
      
      <h2 id="case-studies">Performance Results</h2>
      <p>Over a 3-year period, our optimized portfolio achieved:</p>
      <ul>
        <li>18.5% average annual returns</li>
        <li>Sharpe ratio of 1.8</li>
        <li>Maximum drawdown limited to 8%</li>
        <li>Outperformed benchmark by 340 basis points</li>
      </ul>
      
      <h2 id="conclusion">Lessons in Scale</h2>
      <p>Managing large-scale real estate portfolios requires systematic approaches to decision-making. Data-driven strategies, combined with deep market knowledge, create sustainable competitive advantages in real estate investment.</p>
    `
  },
  {
    id: 6,
    title: 'The Psychology of User Retention in FinTech',
    excerpt: 'How FinBud AI achieved 87% Day-30 retention through behavioral design principles.',
    category: 'FinTech',
    date: 'February 10, 2024',
    readTime: '6 min read',
    icon: '◎',
    content: `
      <h2 id="introduction">Introduction</h2>
      <p>User retention in FinTech is notoriously challenging. With thousands of financial apps competing for attention, creating sticky user experiences requires deep understanding of behavioral psychology and financial habits.</p>
      
      <h2 id="key-insights">The Psychology of Financial Behavior</h2>
      <p>Gen Z users have unique characteristics when it comes to financial apps:</p>
      <ul>
        <li><strong>Instant Gratification:</strong> They expect immediate value and feedback</li>
        <li><strong>Social Validation:</strong> Community features drive engagement</li>
        <li><strong>Gamification:</strong> Achievement systems increase app stickiness</li>
        <li><strong>Education-First:</strong> They want to learn, not just transact</li>
      </ul>
      
      <h2 id="practical-applications">Our Retention Strategy</h2>
      <p>At FinBud AI, we implemented several key retention mechanisms:</p>
      <ul>
        <li>Personalized financial goals with progress tracking</li>
        <li>Social features allowing users to share achievements</li>
        <li>Educational content delivered just-in-time</li>
        <li>AI-powered insights tailored to individual spending patterns</li>
      </ul>
      
      <h2 id="case-studies">Results and Metrics</h2>
      <p>Our behavioral design approach yielded impressive retention metrics:</p>
      <ul>
        <li>87% Day-30 retention rate</li>
        <li>52% Day-90 retention rate</li>
        <li>Average session length of 8.5 minutes</li>
        <li>3.2x increase in feature adoption</li>
      </ul>
      
      <h2 id="conclusion">The Future of FinTech UX</h2>
      <p>Successful FinTech products don't just solve financial problems—they create positive behavioral change. By understanding the psychology behind financial decision-making, we can build products that genuinely improve users' financial well-being.</p>
    `
  }
]

const article = computed(() => {
  const id = parseInt(route.params.id as string)
  return articles.find(a => a.id === id)
})

const relatedArticles = computed(() => {
  if (!article.value) return []
  return articles
    .filter(a => a.id !== article.value!.id && a.category === article.value!.category)
    .slice(0, 3)
})

const previousArticle = computed(() => {
  if (!article.value) return null
  const currentIndex = articles.findIndex(a => a.id === article.value!.id)
  return currentIndex > 0 ? articles[currentIndex - 1] : null
})

const nextArticle = computed(() => {
  if (!article.value) return null
  const currentIndex = articles.findIndex(a => a.id === article.value!.id)
  return currentIndex < articles.length - 1 ? articles[currentIndex + 1] : null
})

const shareArticle = (platform: string) => {
  const url = window.location.href
  const title = article.value?.title || ''
  
  let shareUrl = ''
  
  switch (platform) {
    case 'twitter':
      shareUrl = `https://twitter.com/intent/tweet?url=${encodeURIComponent(url)}&text=${encodeURIComponent(title)}`
      break
    case 'linkedin':
      shareUrl = `https://www.linkedin.com/sharing/share-offsite/?url=${encodeURIComponent(url)}`
      break
  }
  
  if (shareUrl) {
    window.open(shareUrl, '_blank')
  }
}

const copyArticleLink = async () => {
  try {
    await navigator.clipboard.writeText(window.location.href)
    alert('Article link copied to clipboard!')
  } catch (err) {
    console.error('Failed to copy link:', err)
  }
}

const navigateToArticle = (id: number) => {
  router.push(`/blog/article/${id}`)
}

const subscribe = () => {
  if (email.value) {
    alert('Thank you for subscribing! You will receive weekly insights in your inbox.')
    email.value = ''
  }
}

onMounted(() => {
  // Scroll to top when component mounts
  window.scrollTo(0, 0)
})
</script>

<style scoped>
.article-detail {
  min-height: 100vh;
  background: #ffffff;
  color: #000000;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

/* Article Hero */
.article-hero {
  padding: 8rem 0 4rem;
  background: #f8f9fa;
  border-bottom: 1px solid #e9ecef;
}

.hero-content {
  max-width: 800px;
  margin: 0 auto;
  text-align: center;
}

.article-meta {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 2rem;
  flex-wrap: wrap;
}

.article-category {
  padding: 0.5rem 1rem;
  border-radius: 20px;
  font-size: 0.875rem;
  font-weight: 600;
  color: white;
}

.category-fintech { background: linear-gradient(135deg, #667eea, #764ba2); }
.category-ai/ml { background: linear-gradient(135deg, #f093fb, #f5576c); }
.category-entrepreneurship { background: linear-gradient(135deg, #4facfe, #00f2fe); }
.category-strategy { background: linear-gradient(135deg, #43e97b, #38f9d7); }

.article-date, .read-time {
  color: #666666;
  font-size: 0.875rem;
}

.article-title {
  font-size: 3rem;
  font-weight: 800;
  margin-bottom: 1.5rem;
  line-height: 1.2;
  color: #000000;
}

.article-excerpt {
  font-size: 1.25rem;
  line-height: 1.8;
  color: #555555;
  margin-bottom: 2rem;
}

.author-info {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
  margin-top: 3rem;
}

.author-avatar {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  overflow: hidden;
}

.avatar-placeholder {
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, #667eea, #764ba2);
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-weight: 700;
  font-size: 1.5rem;
}

.author-details {
  text-align: left;
}

.author-name {
  font-size: 1.25rem;
  font-weight: 700;
  margin-bottom: 0.25rem;
  color: #000000;
}

.author-title {
  color: #666666;
  font-size: 0.875rem;
}

/* Article Content */
.article-content {
  padding: 4rem 0;
}

.content-wrapper {
  display: grid;
  grid-template-columns: 1fr 300px;
  gap: 4rem;
  max-width: 1200px;
  margin: 0 auto;
}

.article-body {
  line-height: 1.8;
  font-size: 1.125rem;
}

.article-body :deep(h2) {
  font-size: 2rem;
  font-weight: 700;
  margin: 3rem 0 1.5rem;
  color: #000000;
  border-bottom: 2px solid #e9ecef;
  padding-bottom: 0.5rem;
}

.article-body :deep(h3) {
  font-size: 1.5rem;
  font-weight: 600;
  margin: 2rem 0 1rem;
  color: #333333;
}

.article-body :deep(p) {
  margin-bottom: 1.5rem;
  color: #444444;
}

.article-body :deep(ul) {
  margin: 1.5rem 0;
  padding-left: 2rem;
}

.article-body :deep(li) {
  margin-bottom: 0.75rem;
  color: #444444;
}

.article-body :deep(strong) {
  color: #000000;
  font-weight: 700;
}

/* Sidebar */
.article-sidebar {
  position: sticky;
  top: 2rem;
  height: fit-content;
}

.sidebar-content > div {
  background: #f8f9fa;
  border: 1px solid #e9ecef;
  border-radius: 12px;
  padding: 1.5rem;
  margin-bottom: 2rem;
}

.sidebar-content h3 {
  font-size: 1.25rem;
  font-weight: 700;
  margin-bottom: 1rem;
  color: #000000;
}

.toc-list {
  list-style: none;
  padding: 0;
}

.toc-list li {
  margin-bottom: 0.5rem;
}

.toc-list a {
  color: #666666;
  text-decoration: none;
  transition: color 0.3s ease;
}

.toc-list a:hover {
  color: #000000;
}

.share-buttons {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.share-btn {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.75rem 1rem;
  border: 1px solid #e9ecef;
  border-radius: 8px;
  background: #ffffff;
  color: #333333;
  text-decoration: none;
  transition: all 0.3s ease;
  cursor: pointer;
  font-size: 0.875rem;
}

.share-btn:hover {
  background: #000000;
  color: #ffffff;
  border-color: #000000;
}

.related-articles {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.related-item {
  border: 1px solid #e9ecef;
  border-radius: 8px;
  overflow: hidden;
  transition: transform 0.3s ease;
}

.related-item:hover {
  transform: translateY(-2px);
}

.related-link {
  display: flex;
  align-items: center;
  padding: 1rem;
  text-decoration: none;
  color: inherit;
}

.related-icon {
  width: 40px;
  height: 40px;
  background: #e9ecef;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 1rem;
  font-size: 1.25rem;
}

.related-title {
  font-size: 0.875rem;
  font-weight: 600;
  margin-bottom: 0.25rem;
  color: #000000;
}

.related-category {
  font-size: 0.75rem;
  color: #666666;
}

/* Newsletter CTA */
.newsletter-cta {
  padding: 4rem 0;
  background: #000000;
  color: #ffffff;
}

.cta-content {
  text-align: center;
  max-width: 600px;
  margin: 0 auto;
}

.cta-content h2 {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 1rem;
}

.cta-content p {
  font-size: 1.125rem;
  margin-bottom: 2rem;
  opacity: 0.9;
}

.newsletter-form {
  display: flex;
  gap: 1rem;
  max-width: 400px;
  margin: 0 auto;
}

.email-input {
  flex: 1;
  padding: 1rem;
  border: 1px solid #333333;
  border-radius: 8px;
  font-size: 1rem;
  background: #ffffff;
  color: #000000;
}

.subscribe-btn {
  background: #ffffff;
  color: #000000;
  border: 1px solid #ffffff;
  padding: 1rem 2rem;
  border-radius: 8px;
  cursor: pointer;
  font-weight: 600;
  transition: all 0.3s ease;
}

.subscribe-btn:hover {
  background: transparent;
  color: #ffffff;
}

/* Article Navigation */
.article-navigation {
  padding: 2rem 0;
  background: #f8f9fa;
  border-top: 1px solid #e9ecef;
}

.nav-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.back-to-blog {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: #666666;
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s ease;
}

.back-to-blog:hover {
  color: #000000;
}

.article-nav-buttons {
  display: flex;
  gap: 1rem;
}

.nav-btn {
  background: #ffffff;
  border: 1px solid #e9ecef;
  border-radius: 8px;
  padding: 1rem;
  cursor: pointer;
  transition: all 0.3s ease;
  text-align: left;
  max-width: 200px;
}

.nav-btn:hover {
  border-color: #000000;
}

.nav-label {
  display: block;
  font-size: 0.75rem;
  color: #666666;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 0.25rem;
}

.nav-title {
  display: block;
  font-weight: 600;
  color: #000000;
  line-height: 1.3;
}

.loading-state {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 4rem 2rem;
  text-align: center;
}

.loading-spinner {
  width: 40px;
  height: 40px;
  border: 3px solid #e9ecef;
  border-top: 3px solid #000000;
  border-radius: 50%;
  animation: spin 1s linear infinite;
  margin-bottom: 1rem;
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

/* Responsive Design */
@media (max-width: 968px) {
  .content-wrapper {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .article-sidebar {
    position: static;
  }
  
  .article-title {
    font-size: 2rem;
  }
  
  .newsletter-form {
    flex-direction: column;
  }
  
  .nav-content {
    flex-direction: column;
    gap: 2rem;
  }
  
  .article-nav-buttons {
    flex-direction: column;
    width: 100%;
  }
  
  .nav-btn {
    max-width: none;
  }
}

@media (max-width: 480px) {
  .article-meta {
    flex-direction: column;
    align-items: center;
  }
  
  .author-info {
    flex-direction: column;
    text-align: center;
  }
  
  .author-details {
    text-align: center;
  }
}
</style> 