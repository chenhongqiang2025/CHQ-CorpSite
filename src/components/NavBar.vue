<template>
  <el-menu
    mode="horizontal"
    :default-active="$route.path"
    class="nav-menu"
    router
  >
    <el-menu-item index="/">首页</el-menu-item>
    <el-menu-item index="/contact">联系我们</el-menu-item>
  </el-menu>
</template>

<script>
export default {
  name: 'NavBar'
}
</script>

<style scoped>
.nav-menu {
  justify-content: center;
  box-shadow: 0 2px 12px rgba(0,0,0,0.1);
}
</style>