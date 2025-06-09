<template>
  <div class="about">
    <!-- Hero Section -->
    <section class="relative py-20 bg-gradient-to-br from-gray-950 via-gray-900 to-black">
      <div class="container-responsive">
        <div class="max-w-4xl mx-auto text-center">
          <h1 class="text-5xl md:text-6xl font-bold mb-6 gradient-text">
            Câu chuyện của tôi
          </h1>
          <p class="text-xl text-gray-300 mb-8">
            Hành trình từ một chàng trai 22 tuổi với ước mơ kiến tạo tương lai cho thế hệ trẻ Đông Nam Á
          </p>
        </div>
      </div>
    </section>

    <!-- Personal Story -->
    <section class="section-padding bg-gray-900">
      <div class="container-responsive">
        <div class="grid lg:grid-cols-2 gap-16 items-center">
          <div>
            <h2 class="text-4xl font-bold mb-6">Ai là Bùi Đình Trí?</h2>
            <div class="space-y-6 text-lg text-gray-300">
              <p>
                Tôi là <strong class="text-white">Bùi Đình Trí</strong>, 22 tuổi, hiện đang theo học chuyên ngành 
                <strong class="text-white">Kinh tế định lượng và Khoa học máy tính</strong> tại Mỹ. 
                Với tầm nhìn trở thành người kiến tạo hệ sinh thái tri thức – tài chính – giáo dục, 
                tôi luôn tin rằng công nghệ có thể tạo ra những thay đổi tích cực cho cộng đồng.
              </p>
              <p>
                Hiện tại, tôi đang làm việc với vai trò <strong class="text-white">Corporate Finance Analyst</strong> 
                tại Smithfield (Mỹ), đồng thời là <strong class="text-white">Founder của FinBud AI</strong> - 
                nền tảng tài chính thông minh dành cho Gen Z, và đồng sáng lập 
                <strong class="text-white">YoungPreneur Academy</strong> cùng <strong class="text-white">Pathwise Mentorship</strong>.
              </p>
              <p>
                Hành trình của tôi bắt đầu từ niềm đam mê với phân tích dữ liệu và tài chính. 
                Từ việc giành được <strong class="text-white">Quán quân NestQuant</strong> trong lĩnh vực 
                phân tích định lượng thị trường đến việc nhận học bổng <strong class="text-white">$225,000</strong> 
                tại Macalester College, mỗi thành tựu đều là động lực để tôi tiếp tục theo đuổi ước mơ lớn hơn.
              </p>
            </div>
          </div>
          
          <div class="relative">
            <div class="aspect-square bg-gradient-to-br from-blue-600/20 to-purple-600/20 rounded-2xl flex items-center justify-center">
              <div class="text-center">
                <div class="w-32 h-32 bg-gray-800 rounded-full mx-auto mb-6 flex items-center justify-center">
                  <svg class="w-16 h-16 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"/>
                  </svg>
                </div>
                <p class="text-gray-400 italic">
                  "Ẩn nhu tàng cương – Dĩ tĩnh chế động"
                </p>
              </div>
            </div>
            
            <!-- Floating Elements -->
            <div class="absolute -top-4 -right-4 w-24 h-24 bg-blue-600/10 rounded-full blur-xl animate-float"></div>
            <div class="absolute -bottom-4 -left-4 w-32 h-32 bg-purple-600/10 rounded-full blur-xl animate-float" style="animation-delay: 2s;"></div>
          </div>
        </div>
      </div>
    </section>

    <!-- Core Values -->
    <section class="section-padding bg-black">
      <div class="container-responsive">
        <div class="text-center mb-16">
          <h2 class="text-4xl md:text-5xl font-bold mb-6">Giá trị cốt lõi</h2>
          <p class="text-xl text-gray-300 max-w-3xl mx-auto">
            Những nguyên tắc định hướng mọi quyết định và hành động trong cuộc sống và sự nghiệp
          </p>
        </div>

        <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div class="text-center p-8 rounded-2xl bg-gradient-to-br from-blue-900/20 to-blue-800/20 card-hover">
            <div class="w-20 h-20 bg-blue-600/20 rounded-full flex items-center justify-center mx-auto mb-6">
              <svg class="w-10 h-10 text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"/>
              </svg>
            </div>
            <h3 class="text-2xl font-bold mb-4 text-blue-400">Bản lĩnh</h3>
            <p class="text-gray-300">
              Dũng cảm đối mặt với thử thách, kiên định với mục tiêu và luôn duy trì tinh thần tích cực trong mọi hoàn cảnh.
            </p>
          </div>

          <div class="text-center p-8 rounded-2xl bg-gradient-to-br from-green-900/20 to-green-800/20 card-hover">
            <div class="w-20 h-20 bg-green-600/20 rounded-full flex items-center justify-center mx-auto mb-6">
              <svg class="w-10 h-10 text-green-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"/>
              </svg>
            </div>
            <h3 class="text-2xl font-bold mb-4 text-green-400">Chiến lược</h3>
            <p class="text-gray-300">
              Tư duy dài hạn, lập kế hoạch chu đáo và luôn tìm kiếm những cách tiếp cận sáng tạo để giải quyết vấn đề.
            </p>
          </div>

          <div class="text-center p-8 rounded-2xl bg-gradient-to-br from-purple-900/20 to-purple-800/20 card-hover">
            <div class="w-20 h-20 bg-purple-600/20 rounded-full flex items-center justify-center mx-auto mb-6">
              <svg class="w-10 h-10 text-purple-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"/>
              </svg>
            </div>
            <h3 class="text-2xl font-bold mb-4 text-purple-400">Tận tâm</h3>
            <p class="text-gray-300">
              Đặt lợi ích cộng đồng lên hàng đầu, luôn nỗ lực hết mình và cam kết tạo ra giá trị thực sự cho xã hội.
            </p>
          </div>

          <div class="text-center p-8 rounded-2xl bg-gradient-to-br from-yellow-900/20 to-yellow-800/20 card-hover">
            <div class="w-20 h-20 bg-yellow-600/20 rounded-full flex items-center justify-center mx-auto mb-6">
              <svg class="w-10 h-10 text-yellow-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z"/>
              </svg>
            </div>
            <h3 class="text-2xl font-bold mb-4 text-yellow-400">Hướng thiện</h3>
            <p class="text-gray-300">
              Luôn hướng về điều tốt đẹp, lan tỏa năng lượng tích cực và góp phần xây dựng một thế giới tươi sáng hơn.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- Journey Timeline -->
    <section class="section-padding bg-gray-900">
      <div class="container-responsive">
        <div class="text-center mb-16">
          <h2 class="text-4xl md:text-5xl font-bold mb-6">Hành trình phát triển</h2>
          <p class="text-xl text-gray-300">Những cột mốc quan trọng định hình con người tôi ngày hôm nay</p>
        </div>

        <div class="relative">
          <!-- Timeline Line -->
          <div class="absolute left-1/2 transform -translate-x-1/2 w-1 h-full bg-gradient-to-b from-blue-500 to-purple-500"></div>
          
          <div class="space-y-16">
            <!-- Timeline Item 1 -->
            <div class="relative flex items-center">
              <div class="w-1/2 pr-8 text-right">
                <div class="bg-gray-800/50 p-6 rounded-lg card-hover">
                  <h3 class="text-xl font-bold mb-2 text-blue-400">Học bổng $225,000</h3>
                  <p class="text-gray-300 mb-2">Macalester College - Chủ tịch CLB Đầu tư</p>
                  <p class="text-sm text-gray-400">Khởi đầu hành trình học tập và lãnh đạo tại Mỹ</p>
                </div>
              </div>
              <div class="w-6 h-6 bg-blue-500 rounded-full absolute left-1/2 transform -translate-x-1/2 z-10"></div>
              <div class="w-1/2 pl-8"></div>
            </div>

            <!-- Timeline Item 2 -->
            <div class="relative flex items-center">
              <div class="w-1/2 pr-8"></div>
              <div class="w-6 h-6 bg-green-500 rounded-full absolute left-1/2 transform -translate-x-1/2 z-10"></div>
              <div class="w-1/2 pl-8">
                <div class="bg-gray-800/50 p-6 rounded-lg card-hover">
                  <h3 class="text-xl font-bold mb-2 text-green-400">Quán quân NestQuant</h3>
                  <p class="text-gray-300 mb-2">Phân tích định lượng thị trường</p>
                  <p class="text-sm text-gray-400">Khẳng định năng lực trong lĩnh vực tài chính định lượng</p>
                </div>
              </div>
            </div>

            <!-- Timeline Item 3 -->
            <div class="relative flex items-center">
              <div class="w-1/2 pr-8 text-right">
                <div class="bg-gray-800/50 p-6 rounded-lg card-hover">
                  <h3 class="text-xl font-bold mb-2 text-purple-400">Deloitte & Revantage</h3>
                  <p class="text-gray-300 mb-2">Risk Advisory & Blackstone Portfolio</p>
                  <p class="text-sm text-gray-400">Trải nghiệm thực tế tại các tập đoàn hàng đầu</p>
                </div>
              </div>
              <div class="w-6 h-6 bg-purple-500 rounded-full absolute left-1/2 transform -translate-x-1/2 z-10"></div>
              <div class="w-1/2 pl-8"></div>
            </div>

            <!-- Timeline Item 4 -->
            <div class="relative flex items-center">
              <div class="w-1/2 pr-8"></div>
              <div class="w-6 h-6 bg-yellow-500 rounded-full absolute left-1/2 transform -translate-x-1/2 z-10"></div>
              <div class="w-1/2 pl-8">
                <div class="bg-gray-800/50 p-6 rounded-lg card-hover">
                  <h3 class="text-xl font-bold mb-2 text-yellow-400">Smithfield Finance</h3>
                  <p class="text-gray-300 mb-2">Corporate Finance Analyst</p>
                  <p class="text-sm text-gray-400">Vai trò hiện tại trong phân tích tài chính doanh nghiệp</p>
                </div>
              </div>
            </div>

            <!-- Timeline Item 5 -->
            <div class="relative flex items-center">
              <div class="w-1/2 pr-8 text-right">
                <div class="bg-gray-800/50 p-6 rounded-lg card-hover">
                  <h3 class="text-xl font-bold mb-2 text-blue-400">FinBud AI Founder</h3>
                  <p class="text-gray-300 mb-2">Nền tảng tài chính cho Gen Z</p>
                  <p class="text-sm text-gray-400">Khởi nghiệp với tầm nhìn tài chính thông minh</p>
                </div>
              </div>
              <div class="w-6 h-6 bg-blue-500 rounded-full absolute left-1/2 transform -translate-x-1/2 z-10"></div>
              <div class="w-1/2 pl-8"></div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Skills & Expertise -->
    <section class="section-padding bg-black">
      <div class="container-responsive">
        <div class="text-center mb-16">
          <h2 class="text-4xl md:text-5xl font-bold mb-6">Sở trường & Chuyên môn</h2>
          <p class="text-xl text-gray-300">Những kỹ năng và kiến thức tôi đã tích lũy qua hành trình học tập và làm việc</p>
        </div>

        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
          <!-- Finance & Economics -->
          <div class="p-8 rounded-2xl bg-gradient-to-br from-blue-900/20 to-blue-800/20 card-hover">
            <h3 class="text-2xl font-bold mb-4 text-blue-400">Tài chính & Kinh tế</h3>
            <ul class="space-y-3 text-gray-300">
              <li class="flex items-center">
                <svg class="w-4 h-4 text-blue-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                </svg>
                Corporate Finance Analysis
              </li>
              <li class="flex items-center">
                <svg class="w-4 h-4 text-blue-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                </svg>
                Quantitative Market Analysis
              </li>
              <li class="flex items-center">
                <svg class="w-4 h-4 text-blue-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                </svg>
                Risk Assessment & Management
              </li>
              <li class="flex items-center">
                <svg class="w-4 h-4 text-blue-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                </svg>
                Investment Strategy
              </li>
            </ul>
          </div>

          <!-- Technology -->
          <div class="p-8 rounded-2xl bg-gradient-to-br from-green-900/20 to-green-800/20 card-hover">
            <h3 class="text-2xl font-bold mb-4 text-green-400">Công nghệ</h3>
            <ul class="space-y-3 text-gray-300">
              <li class="flex items-center">
                <svg class="w-4 h-4 text-green-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                </svg>
                AI & Machine Learning
              </li>
              <li class="flex items-center">
                <svg class="w-4 h-4 text-green-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                </svg>
                RAG (Retrieval-Augmented Generation)
              </li>
              <li class="flex items-center">
                <svg class="w-4 h-4 text-green-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                </svg>
                Data Science & Analytics
              </li>
              <li class="flex items-center">
                <svg class="w-4 h-4 text-green-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                </svg>
                Product Development
              </li>
            </ul>
          </div>

          <!-- Leadership -->
          <div class="p-8 rounded-2xl bg-gradient-to-br from-purple-900/20 to-purple-800/20 card-hover">
            <h3 class="text-2xl font-bold mb-4 text-purple-400">Lãnh đạo & Quản lý</h3>
            <ul class="space-y-3 text-gray-300">
              <li class="flex items-center">
                <svg class="w-4 h-4 text-purple-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                </svg>
                Strategic Planning
              </li>
              <li class="flex items-center">
                <svg class="w-4 h-4 text-purple-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                </svg>
                Team Building
              </li>
              <li class="flex items-center">
                <svg class="w-4 h-4 text-purple-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                </svg>
                Cross-cultural Management
              </li>
              <li class="flex items-center">
                <svg class="w-4 h-4 text-purple-400 mr-3" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                </svg>
                Mentorship & Coaching
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- Philosophy & Vision -->
    <section class="section-padding bg-gradient-to-br from-gray-900 to-black">
      <div class="container-responsive">
        <div class="max-w-4xl mx-auto text-center">
          <h2 class="text-4xl md:text-5xl font-bold mb-8">Triết lý sống</h2>
          
          <blockquote class="text-2xl md:text-3xl font-medium text-white/90 mb-8 italic">
            "Ẩn nhu tàng cương – Dĩ tĩnh chế động"
          </blockquote>
          
          <p class="text-xl text-gray-300 mb-8">
            Câu châm ngôn này không chỉ là phương châm sống mà còn là cách tôi tiếp cận mọi thử thách trong cuộc sống. 
            <strong class="text-white">Ẩn nhu</strong> - khiêm tốn nhưng luôn sẵn sàng, 
            <strong class="text-white">tàng cương</strong> - ẩn chứa sức mạnh nội tại, 
            <strong class="text-white">dĩ tĩnh chế động</strong> - dùng sự bình tĩnh để đối phó với mọi biến động.
          </p>
          
          <div class="grid md:grid-cols-3 gap-8 mt-12">
            <div class="text-center">
              <h3 class="text-xl font-bold mb-4 text-blue-400">Học hỏi không ngừng</h3>
              <p class="text-gray-300">Luôn duy trì tinh thần học sinh, không ngừng tìm hiểu và cập nhật kiến thức mới.</p>
            </div>
            <div class="text-center">
              <h3 class="text-xl font-bold mb-4 text-green-400">Tạo ra giá trị</h3>
              <p class="text-gray-300">Mọi hành động đều hướng đến việc tạo ra giá trị thiết thực cho cộng đồng và xã hội.</p>
            </div>
            <div class="text-center">
              <h3 class="text-xl font-bold mb-4 text-purple-400">Kết nối & Chia sẻ</h3>
              <p class="text-gray-300">Tin tưởng vào sức mạnh của việc kết nối và sẵn sàng chia sẻ kiến thức với mọi người.</p>
            </div>
          </div>
          
          <div class="mt-12">
            <router-link 
              to="/contact" 
              class="inline-flex items-center bg-white text-black px-8 py-3 rounded-lg font-medium hover:bg-gray-200 transition-all duration-300 group"
            >
              Kết nối với tôi
              <svg class="ml-2 w-4 h-4 group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"/>
              </svg>
            </router-link>
          </div>
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
.about {
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
