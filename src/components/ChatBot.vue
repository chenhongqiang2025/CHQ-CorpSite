<template>
  <div class="chat-container">
    <div class="chat-icon" @click="toggleChat">
      <el-icon :size="30"><ChatDotRound /></el-icon>
    </div>

    <div v-if="showChat" class="chat-window">
      <div class="chat-header">
        <h3>ASK CHQ AI</h3>
        <el-button type="text" @click="toggleChat">
          <el-icon><Close /></el-icon>
        </el-button>
      </div>

      <div class="chat-messages">
        <div v-for="(msg, index) in messages" :key="index" class="message" :class="{ 'ai-message': msg.role === 'ai' }">
          {{ msg.content }}
        </div>
      </div>

      <div class="chat-input">
        <el-input
          v-model="inputMessage"
          placeholder="请输入您的问题..."
          @keyup.enter="sendMessage"
        >
          <template #append>
            <el-button :icon="Promotion" @click="sendMessage" />
          </template>
        </el-input>
      </div>
    </div>
  </div>
</template>

<script>
import { ChatDotRound, Close, Promotion } from '@element-plus/icons-vue'

export default {
  name: 'ChatBot',
  data() {
    return {
      showChat: false,
      inputMessage: '',
      messages: [
        { role: 'ai', content: '您好！我是CHQ AI助手，请问有什么可以帮您？' }
      ]
    }
  },
  methods: {
    toggleChat() {
      this.showChat = !this.showChat
    },
    sendMessage() {
      if (!this.inputMessage.trim()) return

      this.messages.push({ role: 'user', content: this.inputMessage })
      this.inputMessage = ''

      setTimeout(() => {
        this.messages.push({
          role: 'ai',
          content: '这是一个示例回复，后续可接入大语言模型API'
        })
      }, 1000)
    }
  },
  components: { ChatDotRound, Close, Promotion }
}
</script>

<style scoped>
.chat-container {
  position: fixed;
  bottom: 40px;
  right: 40px;
  z-index: 999;
}

.chat-icon {
  background: #2563eb;
  color: white;
  width: 60px;
  height: 60px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  transition: transform 0.3s;
}

.chat-icon:hover {
  transform: scale(1.1);
}

.chat-window {
  width: 400px;
  height: 600px;
  background: white;
  border-radius: 12px;
  box-shadow: 0 10px 15px rgba(0,0,0,0.1);
  display: flex;
  flex-direction: column;
}

.chat-header {
  padding: 16px;
  background: #1a1a1a;
  color: white;
  border-radius: 12px 12px 0 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.chat-messages {
  flex: 1;
  padding: 16px;
  overflow-y: auto;
}

.message {
  background: #f1f5f9;
  padding: 12px;
  border-radius: 8px;
  margin-bottom: 12px;
}

.ai-message {
  background: #2563eb;
  color: white;
}

.chat-input {
  padding: 16px;
  border-top: 1px solid #e2e8f0;
}
</style>