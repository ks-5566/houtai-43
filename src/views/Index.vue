<template>
  <el-container>
  <el-header>
      <Header/>
  </el-header>
  <el-container>
    <el-aside width="200px">
      <!-- 侧边栏组件 -->
        <Aside/>
    </el-aside>
    <el-main>Main</el-main>
  </el-container>
</el-container>
</template>

<script>
// 导入头部组件
import Header from "@/components/Header.vue"
// 导入侧边栏组件
import Aside from "@/components/Aside.vue"
export default {
  // 注册组件
  components:{
    Header,
    Aside
  }
}
</script>
<style scoped lang="less">
  .el-aside {
    background-color: #D3DCE6;
    color: #333;
    text-align: center;
  }
  
  .el-main {
    background-color: #E9EEF3;
    color: #333;
    text-align: center;

  }
  
  #app > .el-container {
    height: 100vh;
    min-width: 1100px;
    min-height: 1000px;
  }
</style>