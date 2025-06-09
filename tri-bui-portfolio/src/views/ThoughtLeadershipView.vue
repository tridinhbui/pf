<template>
  <div class="thought-leadership">
    <!-- Hero Section -->
    <section class="relative py-20 bg-gradient-to-br from-gray-950 via-gray-900 to-black">
      <div class="container-responsive">
        <div class="max-w-4xl mx-auto text-center">
          <h1 class="text-5xl md:text-6xl font-bold mb-6 gradient-text">Thought Leadership</h1>
          <p class="text-xl text-gray-300 mb-8">
            Góc nhìn chiến lược về tài chính, công nghệ và xu hướng tương lai
          </p>
        </div>
      </div>
    </section>

    <!-- Featured Articles -->
    <section class="section-padding bg-gray-900">
      <div class="container-responsive">
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold mb-6">Bài viết nổi bật</h2>
          <p class="text-xl text-gray-300">Những phân tích sâu sắc về thị trường và công nghệ</p>
        </div>

        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
          <article class="bg-gray-800/50 rounded-xl overflow-hidden card-hover">
            <div class="h-48 bg-gradient-to-br from-blue-600/20 to-blue-400/20 flex items-center justify-center">
              <svg class="w-16 h-16 text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M13 10V3L4 14h7v7l9-11h-7z"/>
              </svg>
            </div>
            <div class="p-6">
              <h3 class="text-xl font-bold mb-3 text-blue-400">AI trong FinTech: Cơ hội cho Gen Z</h3>
              <p class="text-gray-300 mb-4">Phân tích xu hướng ứng dụng AI trong lĩnh vực tài chính và cơ hội cho thế hệ trẻ...</p>
              <div class="flex items-center justify-between">
                <span class="text-sm text-gray-400">15/03/2024</span>
                <span class="text-blue-400 text-sm">5 phút đọc</span>
              </div>
            </div>
          </article>

          <article class="bg-gray-800/50 rounded-xl overflow-hidden card-hover">
            <div class="h-48 bg-gradient-to-br from-green-600/20 to-green-400/20 flex items-center justify-center">
              <svg class="w-16 h-16 text-green-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z"/>
              </svg>
            </div>
            <div class="p-6">
              <h3 class="text-xl font-bold mb-3 text-green-400">Khởi nghiệp tại Đông Nam Á: Bài học từ thực tế</h3>
              <p class="text-gray-300 mb-4">Kinh nghiệm xây dựng startup trong bối cảnh thị trường khu vực...</p>
              <div class="flex items-center justify-between">
                <span class="text-sm text-gray-400">08/03/2024</span>
                <span class="text-green-400 text-sm">7 phút đọc</span>
              </div>
            </div>
          </article>

          <article class="bg-gray-800/50 rounded-xl overflow-hidden card-hover">
            <div class="h-48 bg-gradient-to-br from-purple-600/20 to-purple-400/20 flex items-center justify-center">
              <svg class="w-16 h-16 text-purple-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"/>
              </svg>
            </div>
            <div class="p-6">
              <h3 class="text-xl font-bold mb-3 text-purple-400">Tương lai giáo dục tài chính tại Việt Nam</h3>
              <p class="text-gray-300 mb-4">Định hướng phát triển hệ sinh thái giáo dục tài chính cho người trẻ...</p>
              <div class="flex items-center justify-between">
                <span class="text-sm text-gray-400">01/03/2024</span>
                <span class="text-purple-400 text-sm">6 phút đọc</span>
              </div>
            </div>
          </article>
        </div>
      </div>
    </section>

    <!-- Speaking & Events -->
    <section class="section-padding bg-black">
      <div class="container-responsive">
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold mb-6">Diễn giả & Sự kiện</h2>
          <p class="text-xl text-gray-300">Chia sẻ kiến thức tại các hội thảo và sự kiện</p>
        </div>

        <div class="space-y-8">
          <div class="bg-gray-800/50 p-8 rounded-xl card-hover flex items-center justify-between">
            <div>
              <h3 class="text-2xl font-bold mb-2 text-blue-400">FinTech Innovation Summit 2024</h3>
              <p class="text-gray-300 mb-2">Keynote: "AI-Driven Financial Services for Gen Z"</p>
              <p class="text-gray-400">Singapore • 20/04/2024</p>
            </div>
            <div class="text-right">
              <span class="px-4 py-2 bg-blue-600/20 text-blue-400 rounded-full">Keynote</span>
            </div>
          </div>

          <div class="bg-gray-800/50 p-8 rounded-xl card-hover flex items-center justify-between">
            <div>
              <h3 class="text-2xl font-bold mb-2 text-green-400">Vietnam Startup Week</h3>
              <p class="text-gray-300 mb-2">Panel Discussion: "Building Fintech Startups in Southeast Asia"</p>
              <p class="text-gray-400">Ho Chi Minh City • 15/03/2024</p>
            </div>
            <div class="text-right">
              <span class="px-4 py-2 bg-green-600/20 text-green-400 rounded-full">Panel</span>
            </div>
          </div>

          <div class="bg-gray-800/50 p-8 rounded-xl card-hover flex items-center justify-between">
            <div>
              <h3 class="text-2xl font-bold mb-2 text-purple-400">Young Leaders Forum</h3>
              <p class="text-gray-300 mb-2">Workshop: "Strategic Thinking for Young Entrepreneurs"</p>
              <p class="text-gray-400">Hanoi • 05/02/2024</p>
            </div>
            <div class="text-right">
              <span class="px-4 py-2 bg-purple-600/20 text-purple-400 rounded-full">Workshop</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Insights & Predictions -->
    <section class="section-padding bg-gray-900">
      <div class="container-responsive">
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold mb-6">Góc nhìn chiến lược</h2>
          <p class="text-xl text-gray-300">Dự báo và phân tích xu hướng</p>
        </div>

        <div class="grid md:grid-cols-2 gap-12">
          <div>
            <h3 class="text-2xl font-bold mb-6 text-blue-400">Công nghệ & Tài chính</h3>
            <div class="space-y-6">
              <div class="border-l-4 border-blue-400 pl-6">
                <h4 class="font-bold mb-2">AI sẽ thay đổi cách Gen Z quản lý tài chính</h4>
                <p class="text-gray-300">Trong 5 năm tới, AI sẽ trở thành trợ lý tài chính cá nhân chủ đạo cho thế hệ trẻ.</p>
              </div>
              <div class="border-l-4 border-blue-400 pl-6">
                <h4 class="font-bold mb-2">Blockchain và DeFi tại Đông Nam Á</h4>
                <p class="text-gray-300">Khu vực sẽ trở thành hub phát triển DeFi nhờ dân số trẻ và adoption công nghệ cao.</p>
              </div>
            </div>
          </div>
          
          <div>
            <h3 class="text-2xl font-bold mb-6 text-green-400">Khởi nghiệp & Giáo dục</h3>
            <div class="space-y-6">
              <div class="border-l-4 border-green-400 pl-6">
                <h4 class="font-bold mb-2">Giáo dục kỹ năng mềm sẽ là then chốt</h4>
                <p class="text-gray-300">Soft skills như tư duy phản biện và EQ sẽ quyết định thành công trong thời đại AI.</p>
              </div>
              <div class="border-l-4 border-green-400 pl-6">
                <h4 class="font-bold mb-2">Mô hình mentorship sẽ được số hóa</h4>
                <p class="text-gray-300">Nền tảng AI matching sẽ cách mạng hóa cách kết nối mentor và mentee.</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Newsletter Signup -->
    <section class="section-padding bg-gradient-to-r from-blue-900/20 to-purple-900/20">
      <div class="container-responsive text-center">
        <h2 class="text-4xl font-bold mb-6">Nhận insights mới nhất</h2>
        <p class="text-xl text-gray-300 mb-8 max-w-3xl mx-auto">
          Đăng ký để nhận những phân tích và dự báo mới nhất về công nghệ, tài chính và khởi nghiệp.
        </p>
        <div class="max-w-md mx-auto flex gap-4">
          <input 
            type="email" 
            placeholder="Email của bạn" 
            class="flex-1 px-4 py-3 rounded-lg bg-gray-800 text-white border border-gray-600 focus:border-blue-400 focus:outline-none"
          >
          <button class="bg-white text-black px-6 py-3 rounded-lg font-medium hover:bg-gray-200 transition-all duration-300">
            Đăng ký
          </button>
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
.thought-leadership {
  line-height: 1.6;
}

.gradient-text {
  background: linear-gradient(135deg, #ffffff 0%, #a8a8a8 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
</style> 