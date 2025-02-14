<template>
  <div class="home-page">
    <NavBar />
    <div class="hero-banner">
      <h1>ASK CHQ 智能科技</h1>
      <p>引领企业数字化未来</p>
      <el-button type="primary" size="large" @click="$router.push('/contact')">
        立即咨询
      </el-button>
    </div>
    <ChatBot />
  </div>
</template>

<script>
import NavBar from '@/components/NavBar.vue'
import ChatBot from '@/components/ChatBot.vue'

export default {
  name: 'HomePage',
  components: { NavBar, ChatBot }
}
</script>

<style scoped>
.hero-banner {
  background: linear-gradient(135deg, #1e3a8a, #2563eb);
  color: white;
  text-align: center;
  padding: 120px 20px;
}

.home-page {
  min-height: 100vh;
}
</style>