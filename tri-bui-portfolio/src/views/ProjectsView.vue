<template>
  <div class="projects">
    <!-- Hero Section -->
    <section class="relative py-20 bg-gradient-to-br from-gray-950 via-gray-900 to-black">
      <div class="container-responsive">
        <div class="max-w-4xl mx-auto text-center">
          <h1 class="text-5xl md:text-6xl font-bold mb-6 gradient-text">Dự án & Sáng kiến</h1>
          <p class="text-xl text-gray-300 mb-8">
            Những sản phẩm và dự án tạo nên tác động tích cực cho cộng đồng
          </p>
        </div>
      </div>
    </section>

    <!-- Featured Projects -->
    <section class="section-padding bg-gray-900">
      <div class="container-responsive">
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold mb-6">Dự án nổi bật</h2>
          <p class="text-xl text-gray-300">Những sản phẩm định hình tương lai tài chính và giáo dục</p>
        </div>

        <div class="space-y-16">
          <!-- FinBud AI -->
          <div class="grid lg:grid-cols-2 gap-12 items-center">
            <div>
              <h3 class="text-4xl font-bold mb-6 text-blue-400">FinBud AI</h3>
              <p class="text-xl text-gray-300 mb-6">
                Nền tảng tài chính cá nhân thông minh dành cho Gen Z, tích hợp AI để tư vấn đầu tư và quản lý tài chính một cách hiệu quả.
              </p>
              <ul class="space-y-3 text-gray-300 mb-8">
                <li class="flex items-center">
                  <svg class="w-5 h-5 text-blue-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                  </svg>
                  Thuật toán AI tư vấn đầu tư cá nhân hóa
                </li>
                <li class="flex items-center">
                  <svg class="w-5 h-5 text-blue-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                  </svg>
                  Giao diện thân thiện với Gen Z
                </li>
                <li class="flex items-center">
                  <svg class="w-5 h-5 text-blue-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                  </svg>
                  Tích hợp với hệ thống ngân hàng
                </li>
                <li class="flex items-center">
                  <svg class="w-5 h-5 text-blue-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                  </svg>
                  Giáo dục tài chính tương tác
                </li>
              </ul>
              <div class="flex flex-wrap gap-3">
                <span class="px-4 py-2 bg-blue-600/20 text-blue-400 rounded-full">AI/ML</span>
                <span class="px-4 py-2 bg-blue-600/20 text-blue-400 rounded-full">FinTech</span>
                <span class="px-4 py-2 bg-blue-600/20 text-blue-400 rounded-full">React Native</span>
                <span class="px-4 py-2 bg-blue-600/20 text-blue-400 rounded-full">Python</span>
              </div>
            </div>
            <div class="relative">
              <div class="aspect-square bg-gradient-to-br from-blue-600/20 to-blue-400/20 rounded-2xl p-8 flex items-center justify-center">
                <svg class="w-32 h-32 text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M13 10V3L4 14h7v7l9-11h-7z"/>
                </svg>
              </div>
            </div>
          </div>

          <!-- YoungPreneur Academy -->
          <div class="grid lg:grid-cols-2 gap-12 items-center">
            <div class="order-2 lg:order-1 relative">
              <div class="aspect-square bg-gradient-to-br from-green-600/20 to-green-400/20 rounded-2xl p-8 flex items-center justify-center">
                <svg class="w-32 h-32 text-green-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.746 0 3.332.477 4.5 1.253v13C19.832 18.477 18.246 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"/>
                </svg>
              </div>
            </div>
            <div class="order-1 lg:order-2">
              <h3 class="text-4xl font-bold mb-6 text-green-400">YoungPreneur Academy</h3>
              <p class="text-xl text-gray-300 mb-6">
                Chương trình đào tạo kỹ năng khởi nghiệp và lãnh đạo cho thế hệ trẻ Việt Nam, kết nối với mạng lưới mentor và nhà đầu tư quốc tế.
              </p>
              <ul class="space-y-3 text-gray-300 mb-8">
                <li class="flex items-center">
                  <svg class="w-5 h-5 text-green-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                  </svg>
                  Chương trình đào tạo 6 tháng
                </li>
                <li class="flex items-center">
                  <svg class="w-5 h-5 text-green-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                  </svg>
                  Mạng lưới 50+ mentor quốc tế
                </li>
                <li class="flex items-center">
                  <svg class="w-5 h-5 text-green-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                  </svg>
                  Quỹ hỗ trợ khởi nghiệp
                </li>
                <li class="flex items-center">
                  <svg class="w-5 h-5 text-green-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                  </svg>
                  Cộng đồng alumni 500+ thành viên
                </li>
              </ul>
              <div class="flex flex-wrap gap-3">
                <span class="px-4 py-2 bg-green-600/20 text-green-400 rounded-full">Education</span>
                <span class="px-4 py-2 bg-green-600/20 text-green-400 rounded-full">Mentorship</span>
                <span class="px-4 py-2 bg-green-600/20 text-green-400 rounded-full">Community</span>
              </div>
            </div>
          </div>

          <!-- Pathwise Mentorship -->
          <div class="grid lg:grid-cols-2 gap-12 items-center">
            <div>
              <h3 class="text-4xl font-bold mb-6 text-purple-400">Pathwise Mentorship</h3>
              <p class="text-xl text-gray-300 mb-6">
                Nền tảng kết nối mentor và mentee, giúp định hướng nghề nghiệp cho sinh viên và người trẻ thông qua AI matching và phương pháp mentoring khoa học.
              </p>
              <ul class="space-y-3 text-gray-300 mb-8">
                <li class="flex items-center">
                  <svg class="w-5 h-5 text-purple-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                  </svg>
                  AI-powered mentor matching
                </li>
                <li class="flex items-center">
                  <svg class="w-5 h-5 text-purple-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                  </svg>
                  Structured mentoring programs
                </li>
                <li class="flex items-center">
                  <svg class="w-5 h-5 text-purple-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                  </svg>
                  Career development tools
                </li>
                <li class="flex items-center">
                  <svg class="w-5 h-5 text-purple-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                  </svg>
                  Progress tracking & analytics
                </li>
              </ul>
              <div class="flex flex-wrap gap-3">
                <span class="px-4 py-2 bg-purple-600/20 text-purple-400 rounded-full">AI Matching</span>
                <span class="px-4 py-2 bg-purple-600/20 text-purple-400 rounded-full">Career Development</span>
                <span class="px-4 py-2 bg-purple-600/20 text-purple-400 rounded-full">Vue.js</span>
              </div>
            </div>
            <div class="relative">
              <div class="aspect-square bg-gradient-to-br from-purple-600/20 to-purple-400/20 rounded-2xl p-8 flex items-center justify-center">
                <svg class="w-32 h-32 text-purple-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z"/>
                </svg>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Other Projects -->
    <section class="section-padding bg-black">
      <div class="container-responsive">
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold mb-6">Dự án khác</h2>
          <p class="text-xl text-gray-300">Những sáng kiến và đóng góp cộng đồng</p>
        </div>

        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div class="bg-gray-800/50 p-6 rounded-xl card-hover">
            <h3 class="text-xl font-bold mb-4 text-blue-400">Investment Club Leadership</h3>
            <p class="text-gray-300 mb-4">Lãnh đạo CLB đầu tư tại Macalester College với 100+ thành viên</p>
            <span class="text-sm text-gray-400">2021-2023</span>
          </div>
          
          <div class="bg-gray-800/50 p-6 rounded-xl card-hover">
            <h3 class="text-xl font-bold mb-4 text-green-400">Quan Analysis Research</h3>
            <p class="text-gray-300 mb-4">Nghiên cứu phân tích định lượng thị trường chứng khoán</p>
            <span class="text-sm text-gray-400">2022-2023</span>
          </div>
          
          <div class="bg-gray-800/50 p-6 rounded-xl card-hover">
            <h3 class="text-xl font-bold mb-4 text-purple-400">Risk Advisory Projects</h3>
            <p class="text-gray-300 mb-4">Tư vấn rủi ro cho các doanh nghiệp tại Deloitte</p>
            <span class="text-sm text-gray-400">2022-2023</span>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA -->
    <section class="section-padding bg-gradient-to-r from-blue-900/20 to-purple-900/20">
      <div class="container-responsive text-center">
        <h2 class="text-4xl font-bold mb-6">Hợp tác cùng phát triển</h2>
        <p class="text-xl text-gray-300 mb-8 max-w-3xl mx-auto">
          Quan tâm đến các dự án? Hãy kết nối để thảo luận cơ hội hợp tác và đầu tư.
        </p>
        <router-link 
          to="/contact" 
          class="bg-white text-black px-8 py-3 rounded-lg font-medium hover:bg-gray-200 transition-all duration-300"
        >
          Liên hệ hợp tác
        </router-link>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import { onMounted } from 'vue'

onMounted(() => {
  // Add any initialization logic here
})
</script>

<style scoped>
.projects {
  line-height: 1.6;
}

.gradient-text {
  background: linear-gradient(135deg, #ffffff 0%, #a8a8a8 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
</style> 