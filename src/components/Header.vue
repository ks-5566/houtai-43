<template>
<div class="header">
     <div class="left">
     <router-link to="/">
     <span class="iconfont iconnew"></span>
     </router-link>
     </div>
     <!-- 下拉菜单 -->
  <el-dropdown trigger="click">
      <span class="el-dropdown-link">
  <div class="user">
      <img src="http://5b0988e595225.cdn.sohucs.com/images/20171013/fec49f59b98041a4a16886893447f746.jpeg" alt="">
      <span>账号昵称</span>
     </div>
     <i class="el-icon-arrow-down el-icon--right"></i>
     </span>
  <el-dropdown-menu slot="dropdown">
    <el-dropdown-item icon="el-icon-delete" @click.native="handleLogout">退出</el-dropdown-item>
  </el-dropdown-menu>
</el-dropdown> 
</div>
</template>

<script>
export default {
    methods: {
        // 退出登录方法
        handleLogout(){
            // 清除本地存储的用户详情数据
            localStorage.removeItem("userInfo");
            // 提示 
            this.$message({
                message: "退出成功",
                type: "success"
            });
            // 退出后应该回到登录页
            this.$router.replace("/login")
        }
    }
};
</script>

<style scoped lang="less">
.header {
    background: #fff;
    line-height: 60px;
    box-shadow: 2px 2px 2px #eee;
    display: flex;
    justify-content: space-between;
}
.iconnew{
          float:left;
          font-size: 80px;
          padding-left: 40px;
          color: #409eff;
      }
      
  .user{
      float: right;
      display: flex;
      align-items: center;
      padding-left: 1000px;
      
  }
  .user img{
      display: block;
      width: 20px;
      height: 20px;
      object-fit: cover;
      border-radius: 50%;
      margin-right: 10px;
  }
  .el-dropdown{
    height: 60px;
}
  .el-dropdown-link {
    cursor: pointer;
    color: #409EFF;
    display: flex;
    align-items: center;
  }
  .el-icon-arrow-down {
    font-size: 12px;
    
  }
  .demonstration{
      display: block;
      color: #8492a6;
      font-size: 14px;
      margin-bottom: 20px;
  }
</style>