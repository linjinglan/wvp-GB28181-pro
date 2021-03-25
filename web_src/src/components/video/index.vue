<template>
  <div class="videoWrap">
    <div class="wrapper rectClass" ref="wrapper">
      <sidebar/>
    </div>
    <div class="video-content">
      <div class="video-div rectClass" id="videoView">
        <player ref="videoPlayer"
                :videoUrl="videoUrl"
                :error="videoError"
                :message="videoError"
                fluent autoplay live/>
      </div>
      <div class="controls-div rectClass" id="controlsView">
        <el-tabs v-model="tabActiveName" @tab-click="tabHandleClick">
          <el-tab-pane label="云台控制" name="media">
            <div :style="{'height': controlsHeight-75+'px', paddingTop: '15px'}">
              <el-row :gutter="20" style="height: 100%">
                <el-col :span="6" class="controls-col">
                  <control/>
                </el-col>
                <el-col :span="18" style="height: 100%">
                  <split-screen/>
                </el-col>
              </el-row>
            </div>
          </el-tab-pane>
          <el-tab-pane label="设置" name="setUp">
            <div :style="{'height': controlsHeight-75+'px'}">
              <set-up/>
            </div>
          </el-tab-pane>
          <el-tab-pane label="录像查询" name="record">
            <div class="videoHistory" :style="{'height': controlsHeight-75+'px'}">
              <video-list :videoHistory="videoHistory"/>
            </div>
          </el-tab-pane>
          <el-tab-pane label="报警录像" name="alarm">
            <div class="videoHistory" :style="{'height': controlsHeight-75+'px'}">
              <video-list :videoHistory="videoHistory"/>
            </div>
          </el-tab-pane>
        </el-tabs>
      </div>
    </div>
  </div>
</template>

<script>
  import BScroll from 'better-scroll'
  import Sidebar from './components/sidebar'
  import Player from './components/player'
  import Control from './components/control'
  import SetUp from './components/setUp'
  import VideoList from './components/videoList'
  import SplitScreen from './components/splitScreen'

  export default {
    components: {
      Sidebar,
      Player,
      Control,
      SetUp,
      VideoList,
      SplitScreen
    },
    data() {
      return {
        videoUrl: 'http://ivi.bupt.edu.cn/hls/cctv1hd.m3u8',
        controlsHeight: 200,
        tabActiveName: 'media',
        controSpeed: 30,
        presetPos: 1,
        cruisingSpeed: 100,
        cruisingTime: 5,
        cruisingGroup: 0,
        scanSpeed: 100,
        scanGroup: 0,
        videoHistory: {
          date: '',
          searchHistoryResult: [{
            name: '腾讯视频',
            filePath: '',
            startTime: '2021-01-12',
            endTime: '2021-01-12'
          }, {
            name: '腾讯视频',
            filePath: '',
            startTime: '2021-01-12',
            endTime: '2021-01-12'
          }, {
            name: '腾讯视频',
            filePath: '',
            startTime: '2021-01-12',
            endTime: '2021-01-12'
          }] //媒体流历史记录搜索结果
        },
        recordsLoading: false,
      }
    },
    mounted() {
      const _self = this
      this.getBoundingClient()
      window.addEventListener('resize', () => {
        _self.getBoundingClient()
      })
      this.$nextTick(() => {
        this.scroll = new BScroll(this.$refs.wrapper, {
          //开启点击事件 默认为false
          click: true, //允许点击事件
          mouseWheel: true, //允许鼠标滚动
          scrollbar: true //显示滚动条
        })
        this.$refs.videoPlayer.play(this.videoUrl)
      })
    },
    methods: {
      getBoundingClient() {
        this.controlsHeight = document.getElementById('controlsView').clientHeight
      },
      tabHandleClick(tab, event) {

      },
      videoError(e) {
        console.log("播放器错误：" + JSON.stringify(e));
      },
      stopPlayRecord: function (callback) {
        this.$refs.videoPlayer.pause();
        this.videoUrl = '';
        // this.$axios({
        //   method: 'get',
        //   url: '/api/playback/' + this.streamId + '/stop'
        // }).then(function (res) {
        //   if (callback) callback()
        // });
      },
      timeFormatter: function (row, column, cellValue, index) {
        return cellValue.split(" ")[1];
      },
    }
  }
</script>

<style lang="scss">
  ::-webkit-scrollbar {
    /*display: none !important;*/
  }

  html {
    background: #05142c;
  }

  .rectClass {
    border: 1px solid #3f8cfe;
    box-sizing: border-box;
    background: url("../../assets/image/video/rect_lt.png") no-repeat top left,
    url("../../assets/image/video/rect_rt.png") no-repeat top right,
    url("../../assets/image/video/rect_lb.png") no-repeat bottom left,
    url("../../assets/image/video/rect_rb.png") no-repeat bottom right;
    background-size: 21px 20px;
  }

  .wrapper {
    width: 20%;
    position: absolute;
    top: 0;
    bottom: 0; /*关键*/
    overflow: hidden;
    z-index: 1;
  }

  .video-content {
    width: calc(80% - 20px);
    position: absolute;
    top: 0;
    bottom: 0; /*关键*/
    right: 0;
    overflow: hidden;
    z-index: 1;

    .video-div {
      width: 100%;
      height: 60%;
    }

    .controls-div {
      width: 100%;
      height: calc(40% - 20px);
      margin-top: 20px;
      padding: 15px;

      .el-tabs__active-bar {
        display: none;
      }

      .el-tabs__nav-wrap {
        overflow: visible !important;
      }

      .el-tabs__nav-wrap::after {
        bottom: -2px;
        height: 1px;
        background-color: #303030;
        z-index: 3;
      }

      .el-tabs__item {
        padding-left: 20px !important;
        padding-right: 20px !important;
        background: #0f1d34;
        color: #fff !important;
        font-weight: normal;

        &.is-active {
          background: #3f8cfe;
        }
      }
    }
  }

  .videoHistory {
    overflow-y: scroll;

    .tableRow {
      background: transparent;
    }

    margin-top: 10px;

    .pickerDate {
      .el-input__inner {
        background-color: transparent;
        border: 1px solid #303030;
        color: #ffffff;
      }
    }

    .videoHistoryTable {
      width: 100%;
      table-layout: fixed;
      border-collapse: collapse;

      th, td {
        color: #ffffff;
        font-weight: normal;
        text-align: left;
      }

      th {
        border-bottom: 1px #303030 solid;
        color: #3f8cfe;
        line-height: 30px;
      }

      td {
        padding: 15px 5px;
      }

      tr {
        transition: background 0.2s;
        transition-timing-function: ease-in-out;

        &:nth-child(even) {
          background: rgb(8, 37, 78);
        }

        &:hover {
          background: rgb(38, 38, 38);
        }
      }
    }
  }

  .videoPagination {
    text-align: right;

    .el-pagination {
      .btn-prev, .btn-next {
        background: transparent;
        color: #fff;
      }

      .el-pager li {
        background: transparent;
        color: #ffffff;
        transition: color 0.2s;

        &.active {
          color: #3f8cfe;
          border: 1px solid #3f8cfe;
          border-radius: 5px;
        }

        &:hover {
          color: #3f8cfe;
        }
      }
    }
  }
  .controls-col{
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    /*background: red;*/
  }

</style>
