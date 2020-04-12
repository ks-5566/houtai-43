<template>
    <div>
        <!-- 左侧栏菜单 -->
        <!-- 导航菜单组件的文档地址：https://element.eleme.cn/#/zh-CN/component/menu#ce-lan -->
        <!-- default-active：默认的高亮栏目，对应的值是菜单组件的index属性 -->
        <!-- 侧边栏 -->
     <el-menu
      default-active="1"
      class="el-menu-vertical-demo"
      background-color="#545c64"
      text-color="#fff"
      active-text-color="#ffd04b">
      <el-submenu index="1">
        <template slot="title">
          <i class="el-icon-s-order"></i>
          <span>文章管理</span>
        </template>
          <el-menu-item index="1-1-1">文章列表</el-menu-item>
          <el-menu-item index="1-1-2">文章发布</el-menu-item>
      </el-submenu>
    </el-menu>
</div>
</template>

<script>
export default {
}
</script>

<style scoped lang="less">
.el-menu{
    border-right: none;
}
</style>