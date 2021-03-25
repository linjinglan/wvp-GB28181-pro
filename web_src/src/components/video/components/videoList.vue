<template>
  <div>
    <div style="text-align: right">
      <el-date-picker class="pickerDate" size="mini" v-model="videoHistory.date" type="date"
                      value-format="yyyy-MM-dd" placeholder="请选择日期" @change="queryRecords()"></el-date-picker>
    </div>
    <table class="videoHistoryTable">
      <thead>
      <th>名称</th>
      <th>文件</th>
      <th>开始时间</th>
      <th>结束时间</th>
      <th>操作</th>
      </thead>
      <tbody>
      <tr v-for="(item, index) of videoHistory.searchHistoryResult" :key="index">
        <td>{{item.name}}</td>
        <td>{{item.filePath}}</td>
        <td>{{item.startTime}}</td>
        <td>{{item.endTime}}</td>
        <td>
          <el-button icon="el-icon-video-play" type="primary" size="mini" @click="playRecord(scope.row)">播放</el-button>
          <el-button icon="el-icon-download" type="primary" size="mini" @click="downloadRecord(scope.row)">下载</el-button>
        </td>
      </tr>
      </tbody>
    </table>
    <div class="videoPagination">
      <el-pagination
        layout="prev, pager, next"
        :total="1000">
      </el-pagination>
    </div>
  </div>
</template>

<script>
  export default {
    name: "index",
    props: {
      videoHistory: {
        type: Object
      }
    },
    mounted() {

    },
    methods: {
      queryRecords() {

      },
      playRecord(item) {

      },
      downloadRecord(item) {

      }
    }
  }
</script>

<style scoped>

</style>
