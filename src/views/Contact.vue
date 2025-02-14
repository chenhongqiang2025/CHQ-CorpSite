<template>
  <div class="contact-page">
    <NavBar />
    <h1>联系我们</h1>
    <el-form :model="form" label-width="120px">
      <el-form-item label="姓名">
        <el-input v-model="form.name" />
      </el-form-item>
      <el-form-item label="邮箱">
        <el-input v-model="form.email" />
      </el-form-item>
      <el-form-item label="留言">
        <el-input v-model="form.message" type="textarea" />
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="submitForm">提交</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
import NavBar from '@/components/NavBar.vue'

export default {
  name: 'ContactPage',
  data() {
    return {
      form: {
        name: '',
        email: '',
        message: ''
      }
    }
  },
  methods: {
    submitForm() {
      alert('表单已提交！')
    }
  },
  components: { NavBar }
}
</script>

<style scoped>
.contact-page {
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem;
}
</style>