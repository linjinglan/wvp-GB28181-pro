<template>
  <div>
    <el-submenu :index="item.id" v-if="item.children && item.children.length">
      <template slot="title">
        <span slot="title" class="titleHover">{{item.title}}</span>
      </template>
      <sidebar-item v-for="(child,index) in item.children" :key="index" :item="child"/>
    </el-submenu>
    <el-menu-item :index="item.id" v-else>
      <span slot="title" class="titleHover">{{item.title}}</span>
    </el-menu-item>
  </div>
</template>

<script>
  export default {
    name: "SidebarItem",
    props: {
      item: {
        type: Object,
        required: true
      }
    }
  }
</script>

<style scoped>
  >>> .el-menu-item {
    height: auto !important;
    line-height: 30px !important;
  }

  >>> .el-submenu__title {
    height: auto !important;
    line-height: 30px !important;
  }

  .titleHover {
    padding: 5px 7px;
  }

  .titleHover:hover {
    background: #19263d;
    border-radius: 3px;
  }

  .itemActive {
    background: #06264f;
  }
</style>
