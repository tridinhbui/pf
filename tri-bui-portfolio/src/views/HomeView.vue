<script setup lang="ts">
import { onMounted } from 'vue'
</script>

<template>
  <div class="home">
    <!-- Hero Section -->
    <section class="relative min-h-screen flex items-center justify-center overflow-hidden bg-gradient-to-br from-gray-950 via-gray-900 to-black">
      <!-- Background Effects -->
      <div class="absolute inset-0">
        <div class="absolute top-1/4 left-1/4 w-96 h-96 bg-blue-600/10 rounded-full blur-3xl animate-float"></div>
        <div class="absolute bottom-1/4 right-1/4 w-80 h-80 bg-purple-600/10 rounded-full blur-3xl animate-float" style="animation-delay: 2s;"></div>
        <div class="absolute inset-0 bg-[url('data:image/svg+xml,%3Csvg width="60" height="60" viewBox="0 0 60 60" xmlns="http://www.w3.org/2000/svg"%3E%3Cg fill="none" fill-rule="evenodd"%3E%3Cg fill="%23ffffff" fill-opacity="0.02"%3E%3Ccircle cx="3" cy="3" r="1"/%3E%3C/g%3E%3C/g%3E%3C/svg%3E')] opacity-20"></div>
      </div>

      <!-- Hero Content -->
      <div class="relative z-10 text-center max-w-5xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="animate-fade-in">
          <h1 class="text-5xl md:text-7xl font-bold mb-6 gradient-text">
            Bùi Đình Trí
          </h1>
          <p class="text-xl md:text-2xl text-gray-300 mb-4 font-light">
            Nhà lãnh đạo trẻ • Chiến lược gia • Người kiến tạo tương lai
          </p>
          <p class="text-lg text-gray-400 mb-8 max-w-3xl mx-auto">
            22 tuổi, khát vọng tạo nên những giá trị trường tồn thông qua công nghệ, tài chính, và giáo dục. 
            Hiện tại là Corporate Finance Analyst tại Smithfield (Mỹ) và Founder của FinBud AI.
          </p>
          
          <!-- Quote -->
          <blockquote class="text-xl md:text-2xl font-medium text-white/90 mb-12 italic">
            "Ẩn nhu tàng cương – Dĩ tĩnh chế động"
          </blockquote>
          
          <!-- CTA Buttons -->
          <div class="flex flex-col sm:flex-row gap-4 justify-center">
            <router-link 
              to="/about" 
              class="bg-white text-black px-8 py-3 rounded-lg font-medium hover:bg-gray-200 transition-all duration-300 inline-flex items-center justify-center group"
            >
              Khám phá hành trình
              <svg class="ml-2 w-4 h-4 group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"/>
              </svg>
            </router-link>
            <router-link 
              to="/contact" 
              class="border border-white text-white px-8 py-3 rounded-lg font-medium hover:bg-white hover:text-black transition-all duration-300"
            >
              Kết nối hợp tác
            </router-link>
          </div>
        </div>
      </div>

      <!-- Scroll Indicator -->
      <div class="absolute bottom-8 left-1/2 transform -translate-x-1/2 animate-bounce">
        <svg class="w-6 h-6 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"/>
        </svg>
      </div>
    </section>

    <!-- Vision Section -->
    <section class="section-padding bg-gray-900">
      <div class="container-responsive">
        <div class="text-center mb-16">
          <h2 class="text-4xl md:text-5xl font-bold mb-6">Tầm nhìn & Sứ mệnh</h2>
          <p class="text-xl text-gray-300 max-w-3xl mx-auto">
            Trở thành người kiến tạo hệ sinh thái tri thức – tài chính – giáo dục dành cho thế hệ trẻ Đông Nam Á
          </p>
        </div>

        <div class="grid md:grid-cols-3 gap-8">
          <div class="text-center p-8 rounded-2xl bg-gray-800/50 backdrop-blur card-hover">
            <div class="w-16 h-16 bg-blue-600/20 rounded-full flex items-center justify-center mx-auto mb-6">
              <svg class="w-8 h-8 text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"/>
              </svg>
            </div>
            <h3 class="text-xl font-semibold mb-4">Đổi mới</h3>
            <p class="text-gray-300">Kết hợp công nghệ AI, Machine Learning với tài chính và giáo dục để tạo ra những giải pháp tiên tiến.</p>
          </div>

          <div class="text-center p-8 rounded-2xl bg-gray-800/50 backdrop-blur card-hover">
            <div class="w-16 h-16 bg-green-600/20 rounded-full flex items-center justify-center mx-auto mb-6">
              <svg class="w-8 h-8 text-green-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z"/>
              </svg>
            </div>
            <h3 class="text-xl font-semibold mb-4">Lãnh đạo</h3>
            <p class="text-gray-300">Xây dựng và dẫn dắt các đội nhóm đa quốc gia, tạo ra những sản phẩm có tác động xã hội tích cực.</p>
          </div>

          <div class="text-center p-8 rounded-2xl bg-gray-800/50 backdrop-blur card-hover">
            <div class="w-16 h-16 bg-purple-600/20 rounded-full flex items-center justify-center mx-auto mb-6">
              <svg class="w-8 h-8 text-purple-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"/>
              </svg>
            </div>
            <h3 class="text-xl font-semibold mb-4">Tận tâm</h3>
            <p class="text-gray-300">Cam kết phục vụ cộng đồng và tạo ra những giá trị bền vững cho thế hệ trẻ Việt Nam và Đông Nam Á.</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Achievements Highlight -->
    <section class="section-padding bg-black">
      <div class="container-responsive">
        <div class="text-center mb-16">
          <h2 class="text-4xl md:text-5xl font-bold mb-6">Thành tựu nổi bật</h2>
          <p class="text-xl text-gray-300">Những cột mốc quan trọng trong hành trình 22 tuổi</p>
        </div>

        <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div class="text-center">
            <div class="text-4xl font-bold text-blue-400 mb-2">$225K</div>
            <div class="text-gray-300">Học bổng tại Macalester College</div>
          </div>
          <div class="text-center">
            <div class="text-4xl font-bold text-green-400 mb-2">#1</div>
            <div class="text-gray-300">Quán quân NestQuant</div>
          </div>
          <div class="text-center">
            <div class="text-4xl font-bold text-purple-400 mb-2">3+</div>
            <div class="text-gray-300">Startup đồng sáng lập</div>
          </div>
          <div class="text-center">
            <div class="text-4xl font-bold text-yellow-400 mb-2">22</div>
            <div class="text-gray-300">Tuổi với tầm nhìn lớn</div>
          </div>
        </div>
      </div>
    </section>

    <!-- Featured Projects -->
    <section class="section-padding bg-gray-900">
      <div class="container-responsive">
        <div class="text-center mb-16">
          <h2 class="text-4xl md:text-5xl font-bold mb-6">Dự án tiêu biểu</h2>
          <p class="text-xl text-gray-300">Những sản phẩm tạo nên tác động tích cực</p>
        </div>

        <div class="grid md:grid-cols-3 gap-8">
          <div class="group relative overflow-hidden rounded-2xl bg-gradient-to-br from-blue-900/20 to-blue-800/20 p-8 card-hover">
            <div class="absolute inset-0 bg-gradient-to-br from-blue-600/10 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
            <div class="relative z-10">
              <h3 class="text-2xl font-bold mb-4">FinBud AI</h3>
              <p class="text-gray-300 mb-6">Nền tảng tài chính cá nhân thông minh dành cho Gen Z, tích hợp AI để tư vấn đầu tư và quản lý tài chính.</p>
              <div class="flex items-center text-blue-400 font-medium">
                Tìm hiểu thêm
                <svg class="ml-2 w-4 h-4 group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"/>
                </svg>
              </div>
            </div>
          </div>

          <div class="group relative overflow-hidden rounded-2xl bg-gradient-to-br from-green-900/20 to-green-800/20 p-8 card-hover">
            <div class="absolute inset-0 bg-gradient-to-br from-green-600/10 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
            <div class="relative z-10">
              <h3 class="text-2xl font-bold mb-4">YoungPreneur Academy</h3>
              <p class="text-gray-300 mb-6">Chương trình đào tạo kỹ năng khởi nghiệp và lãnh đạo cho thế hệ trẻ Việt Nam.</p>
              <div class="flex items-center text-green-400 font-medium">
                Tìm hiểu thêm
                <svg class="ml-2 w-4 h-4 group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"/>
                </svg>
              </div>
            </div>
          </div>

          <div class="group relative overflow-hidden rounded-2xl bg-gradient-to-br from-purple-900/20 to-purple-800/20 p-8 card-hover">
            <div class="absolute inset-0 bg-gradient-to-br from-purple-600/10 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
            <div class="relative z-10">
              <h3 class="text-2xl font-bold mb-4">Pathwise Mentorship</h3>
              <p class="text-gray-300 mb-6">Nền tảng kết nối mentor và mentee, giúp định hướng nghề nghiệp cho sinh viên.</p>
              <div class="flex items-center text-purple-400 font-medium">
                Tìm hiểu thêm
                <svg class="ml-2 w-4 h-4 group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"/>
                </svg>
              </div>
            </div>
          </div>
        </div>

        <div class="text-center mt-12">
          <router-link 
            to="/projects" 
            class="inline-flex items-center bg-white text-black px-8 py-3 rounded-lg font-medium hover:bg-gray-200 transition-all duration-300 group"
          >
            Xem tất cả dự án
            <svg class="ml-2 w-4 h-4 group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"/>
            </svg>
          </router-link>
        </div>
      </div>
    </section>

    <!-- Call to Action -->
    <section class="section-padding bg-gradient-to-r from-blue-900/20 to-purple-900/20">
      <div class="container-responsive text-center">
        <h2 class="text-4xl md:text-5xl font-bold mb-6">Kết nối & Hợp tác</h2>
        <p class="text-xl text-gray-300 mb-8 max-w-3xl mx-auto">
          Nếu bạn là nhà đầu tư, cố vấn, hoặc đối tác tiềm năng muốn cùng kiến tạo tương lai, 
          hãy kết nối để chúng ta có thể tạo ra những giá trị ý nghĩa cùng nhau.
        </p>
        <div class="flex flex-col sm:flex-row gap-4 justify-center">
          <router-link 
            to="/contact" 
            class="bg-white text-black px-8 py-3 rounded-lg font-medium hover:bg-gray-200 transition-all duration-300"
          >
            Liên hệ hợp tác
          </router-link>
          <a 
            href="mailto:contact@example.com" 
            class="border border-white text-white px-8 py-3 rounded-lg font-medium hover:bg-white hover:text-black transition-all duration-300"
          >
            Gửi email
          </a>
        </div>
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
.home {
  line-height: 1.6;
}

.gradient-text {
  background: linear-gradient(135deg, #ffffff 0%, #a8a8a8 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

@keyframes float {
  0%, 100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-20px);
  }
}

.animate-float {
  animation: float 6s ease-in-out infinite;
}
</style>
