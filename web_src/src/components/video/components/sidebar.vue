<template>
  <div>
    <el-menu
      default-active="1-4-1"
      class="el-menu-vertical-demo"
      @open="handleOpen"
      @close="handleClose"
      :default-openeds="defaultOpeneds"
      :unique-opened="false"
      :collapse="isCollapse"
      background-color="transparent"
      text-color="white"
      active-text-color="#9999">
      <sidebar-item v-for="(item,index) in list" :key="index" :item="item"/>
    </el-menu>
  </div>
</template>

<script>
  import SidebarItem from '../sidebarItem'

  export default {
    name: "index",
    components: {
      SidebarItem
    },
    data() {
      return {
        isCollapse: false,
        defaultOpeneds: [],
        list: [
          {
            id: "01",
            title: "香洲区",
            children: [
              {
                id: "010",
                title: "核心站点"
              },
              {
                id: "011",
                title: "接入站点",
                children: [
                  {
                    id: "0110",
                    title: "珠海香洲珠宝酒店接入机房1"
                  },
                  {
                    id: "0111",
                    title: "珠海香洲珠宝酒店接入机房2"
                  }
                ]
              }
            ]
          },
          {
            id: "02",
            title: "斗门区",
            children: [
              {
                id: "020",
                title: "汇聚站点"
              },
              {
                id: "021",
                title: "用户站点",
                children: [
                  {
                    id: "0210",
                    title: "珠海斗门珠宝酒店接入机房1"
                  },
                  {
                    id: "0211",
                    title: "珠海斗门珠宝酒店接入机房2"
                  }
                ]
              }
            ]
          }
        ]
      };
    },
    mounted() {
      this.getOpens(this.list)
    },
    methods: {
      getOpens(list) {
        for (let key in list) {
          this.defaultOpeneds.push(list[key].id)
          if (list[key].children) {
            this.getOpens(list[key].children)
          }
        }
      },
      handleOpen(key, keyPath) {
        console.log(key, keyPath);
      },
      handleClose(key, keyPath) {
        console.log(key, keyPath);
      }
    }
  }
</script>

<style scoped>
  >>> .el-menu {
    border-right: none !important;
  }

  >>> .el-menu-item:hover {
    background: transparent !important;
  }

  >>> .el-submenu__title:hover {
    background: transparent !important;
  }
</style>
