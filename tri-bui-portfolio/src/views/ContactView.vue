<template>
  <div class="contact">
    <!-- Hero Section -->
    <section class="relative py-20 bg-gradient-to-br from-gray-950 via-gray-900 to-black">
      <div class="container-responsive">
        <div class="max-w-4xl mx-auto text-center">
          <h1 class="text-5xl md:text-6xl font-bold mb-6 gradient-text">Kết nối & Hợp tác</h1>
          <p class="text-xl text-gray-300 mb-8">
            Hãy liên hệ để thảo luận cơ hội hợp tác, mentoring, hoặc đầu tư
          </p>
        </div>
      </div>
    </section>

    <!-- Contact Options -->
    <section class="section-padding bg-gray-900">
      <div class="container-responsive">
        <div class="grid md:grid-cols-3 gap-8">
          <!-- Collaboration -->
          <div class="text-center p-8 bg-gradient-to-br from-blue-900/20 to-blue-800/20 rounded-2xl card-hover">
            <div class="w-20 h-20 bg-blue-600/20 rounded-full flex items-center justify-center mx-auto mb-6">
              <svg class="w-10 h-10 text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z"/>
              </svg>
            </div>
            <h3 class="text-2xl font-bold mb-4 text-blue-400">Hợp tác dự án</h3>
            <p class="text-gray-300 mb-6">
              Đối với các cơ hội hợp tác trong lĩnh vực FinTech, AI, hoặc giáo dục
            </p>
            <a 
              href="mailto:collaboration@example.com" 
              class="inline-block bg-blue-600 text-white px-6 py-3 rounded-lg hover:bg-blue-700 transition-colors"
            >
              Gửi đề xuất
            </a>
          </div>

          <!-- Investment -->
          <div class="text-center p-8 bg-gradient-to-br from-green-900/20 to-green-800/20 rounded-2xl card-hover">
            <div class="w-20 h-20 bg-green-600/20 rounded-full flex items-center justify-center mx-auto mb-6">
              <svg class="w-10 h-10 text-green-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z"/>
              </svg>
            </div>
            <h3 class="text-2xl font-bold mb-4 text-green-400">Cơ hội đầu tư</h3>
            <p class="text-gray-300 mb-6">
              Dành cho các nhà đầu tư quan tâm đến FinBud AI và các dự án startup
            </p>
            <a 
              href="mailto:investment@example.com" 
              class="inline-block bg-green-600 text-white px-6 py-3 rounded-lg hover:bg-green-700 transition-colors"
            >
              Thảo luận đầu tư
            </a>
          </div>

          <!-- Mentoring -->
          <div class="text-center p-8 bg-gradient-to-br from-purple-900/20 to-purple-800/20 rounded-2xl card-hover">
            <div class="w-20 h-20 bg-purple-600/20 rounded-full flex items-center justify-center mx-auto mb-6">
              <svg class="w-10 h-10 text-purple-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.746 0 3.332.477 4.5 1.253v13C19.832 18.477 18.246 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"/>
              </svg>
            </div>
            <h3 class="text-2xl font-bold mb-4 text-purple-400">Mentoring</h3>
            <p class="text-gray-300 mb-6">
              Tư vấn và định hướng cho sinh viên, người trẻ trong lĩnh vực tài chính và khởi nghiệp
            </p>
            <a 
              href="mailto:mentoring@example.com" 
              class="inline-block bg-purple-600 text-white px-6 py-3 rounded-lg hover:bg-purple-700 transition-colors"
            >
              Đăng ký mentoring
            </a>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Form -->
    <section class="section-padding bg-black">
      <div class="container-responsive">
        <div class="max-w-4xl mx-auto">
          <div class="text-center mb-12">
            <h2 class="text-4xl font-bold mb-6">Gửi tin nhắn</h2>
            <p class="text-xl text-gray-300">Chia sẻ ý tưởng hoặc câu hỏi của bạn</p>
          </div>

          <form class="space-y-6">
            <div class="grid md:grid-cols-2 gap-6">
              <div>
                <label class="block text-sm font-medium mb-2">Họ và tên</label>
                <input 
                  type="text" 
                  class="w-full px-4 py-3 rounded-lg bg-gray-800 text-white border border-gray-600 focus:border-blue-400 focus:outline-none"
                  placeholder="Tên của bạn"
                >
              </div>
              <div>
                <label class="block text-sm font-medium mb-2">Email</label>
                <input 
                  type="email" 
                  class="w-full px-4 py-3 rounded-lg bg-gray-800 text-white border border-gray-600 focus:border-blue-400 focus:outline-none"
                  placeholder="email@example.com"
                >
              </div>
            </div>
            
            <div class="grid md:grid-cols-2 gap-6">
              <div>
                <label class="block text-sm font-medium mb-2">Công ty/Tổ chức</label>
                <input 
                  type="text" 
                  class="w-full px-4 py-3 rounded-lg bg-gray-800 text-white border border-gray-600 focus:border-blue-400 focus:outline-none"
                  placeholder="Tên công ty (tùy chọn)"
                >
              </div>
              <div>
                <label class="block text-sm font-medium mb-2">Loại yêu cầu</label>
                <select class="w-full px-4 py-3 rounded-lg bg-gray-800 text-white border border-gray-600 focus:border-blue-400 focus:outline-none">
                  <option>Hợp tác dự án</option>
                  <option>Cơ hội đầu tư</option>
                  <option>Mentoring</option>
                  <option>Speaking/Workshop</option>
                  <option>Khác</option>
                </select>
              </div>
            </div>

            <div>
              <label class="block text-sm font-medium mb-2">Tiêu đề</label>
              <input 
                type="text" 
                class="w-full px-4 py-3 rounded-lg bg-gray-800 text-white border border-gray-600 focus:border-blue-400 focus:outline-none"
                placeholder="Tiêu đề tin nhắn"
              >
            </div>

            <div>
              <label class="block text-sm font-medium mb-2">Nội dung</label>
              <textarea 
                rows="6" 
                class="w-full px-4 py-3 rounded-lg bg-gray-800 text-white border border-gray-600 focus:border-blue-400 focus:outline-none resize-none"
                placeholder="Chia sẻ chi tiết về ý tưởng, dự án hoặc câu hỏi của bạn..."
              ></textarea>
            </div>

            <div class="text-center">
              <button 
                type="submit" 
                class="bg-white text-black px-8 py-3 rounded-lg font-medium hover:bg-gray-200 transition-all duration-300"
              >
                Gửi tin nhắn
              </button>
            </div>
          </form>
        </div>
      </div>
    </section>

    <!-- Social & Contact Info -->
    <section class="section-padding bg-gray-900">
      <div class="container-responsive">
        <div class="text-center mb-12">
          <h2 class="text-4xl font-bold mb-6">Kết nối qua mạng xã hội</h2>
          <p class="text-xl text-gray-300">Theo dõi để cập nhật những insights và dự án mới nhất</p>
        </div>

        <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
          <!-- LinkedIn -->
          <a 
            href="https://linkedin.com" 
            target="_blank"
            class="flex items-center p-6 bg-blue-600/10 rounded-xl hover:bg-blue-600/20 transition-colors group"
          >
            <svg class="w-8 h-8 text-blue-400 mr-4" fill="currentColor" viewBox="0 0 20 20">
              <path d="M16.338 16.338H13.67V12.16c0-.995-.017-2.277-1.387-2.277-1.39 0-1.601 1.086-1.601 2.207v4.248H8.014v-8.59h2.559v1.174h.037c.356-.675 1.227-1.387 2.526-1.387 2.703 0 3.203 1.778 3.203 4.092v4.711zM5.005 6.575a1.548 1.548 0 11-.003-3.096 1.548 1.548 0 01.003 3.096zm-1.337 9.763H6.34v-8.59H3.667v8.59zM17.668 1H2.328C1.595 1 1 1.581 1 2.298v15.403C1 18.418 1.595 19 2.328 19h15.34c.734 0 1.332-.582 1.332-1.299V2.298C19 1.581 18.402 1 17.668 1z"/>
            </svg>
            <div>
              <h3 class="font-semibold text-blue-400">LinkedIn</h3>
              <p class="text-sm text-gray-400">Professional network</p>
            </div>
          </a>

          <!-- GitHub -->
          <a 
            href="https://github.com" 
            target="_blank"
            class="flex items-center p-6 bg-gray-600/10 rounded-xl hover:bg-gray-600/20 transition-colors group"
          >
            <svg class="w-8 h-8 text-gray-400 mr-4" fill="currentColor" viewBox="0 0 20 20">
              <path fill-rule="evenodd" d="M10 0C4.477 0 0 4.484 0 10.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0110 4.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.203 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.942.359.31.678.921.678 1.856 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0020 10.017C20 4.484 15.522 0 10 0z" clip-rule="evenodd"/>
            </svg>
            <div>
              <h3 class="font-semibold text-gray-400">GitHub</h3>
              <p class="text-sm text-gray-400">Code repositories</p>
            </div>
          </a>

          <!-- Twitter -->
          <a 
            href="https://twitter.com" 
            target="_blank"
            class="flex items-center p-6 bg-blue-400/10 rounded-xl hover:bg-blue-400/20 transition-colors group"
          >
            <svg class="w-8 h-8 text-blue-400 mr-4" fill="currentColor" viewBox="0 0 20 20">
              <path d="M6.29 18.251c7.547 0 11.675-6.253 11.675-11.675 0-.178 0-.355-.012-.53A8.348 8.348 0 0020 3.92a8.19 8.19 0 01-2.357.646 4.118 4.118 0 001.804-2.27 8.224 8.224 0 01-2.605.996 4.107 4.107 0 00-6.993 3.743 11.65 11.65 0 01-8.457-4.287 4.106 4.106 0 001.27 5.477A4.073 4.073 0 01.8 7.713v.052a4.105 4.105 0 003.292 4.022 4.095 4.095 0 01-1.853.07 4.108 4.108 0 003.834 2.85A8.233 8.233 0 010 16.407a11.616 11.616 0 006.29 1.84"/>
            </svg>
            <div>
              <h3 class="font-semibold text-blue-400">Twitter</h3>
              <p class="text-sm text-gray-400">Thoughts & insights</p>
            </div>
          </a>

          <!-- Email -->
          <a 
            href="mailto:contact@example.com"
            class="flex items-center p-6 bg-green-600/10 rounded-xl hover:bg-green-600/20 transition-colors group"
          >
            <svg class="w-8 h-8 text-green-400 mr-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 4.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/>
            </svg>
            <div>
              <h3 class="font-semibold text-green-400">Email</h3>
              <p class="text-sm text-gray-400">Direct contact</p>
            </div>
          </a>
        </div>
      </div>
    </section>

    <!-- Final CTA -->
    <section class="section-padding bg-gradient-to-r from-blue-900/20 to-purple-900/20">
      <div class="container-responsive text-center">
        <h2 class="text-4xl font-bold mb-6">Sẵn sàng bắt đầu cuộc trò chuyện</h2>
        <p class="text-xl text-gray-300 mb-8 max-w-3xl mx-auto">
          Dù bạn có ý tưởng dự án, cơ hội đầu tư, hay chỉ muốn kết nối và học hỏi, 
          tôi luôn sẵn sàng lắng nghe và chia sẻ.
        </p>
        <blockquote class="text-2xl font-medium text-white/90 italic mb-8">
          "Ẩn nhu tàng cương – Dĩ tĩnh chế động"
        </blockquote>
        <p class="text-gray-400">
          Bùi Đình Trí • Founder, Strategist, Young Leader
        </p>
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
.contact {
  line-height: 1.6;
}

.gradient-text {
  background: linear-gradient(135deg, #ffffff 0%, #a8a8a8 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
</style> 