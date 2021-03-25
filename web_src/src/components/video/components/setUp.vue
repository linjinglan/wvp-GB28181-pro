<template>
  <div class="control-panel">
    <el-row :gutter="20" style="height: 100%">
      <el-col :span="4" style="height: 100%">
        <div class="control-zoom">
          <div>
            <i class="el-icon-zoom-in control-zoom-btn"
               @mousedown="ptzCamera(0, 0, 1)" @mouseup="ptzCamera(0, 0, 0)"></i>
            <i class="el-icon-zoom-out control-zoom-btn"
               @mousedown="ptzCamera(0, 0, 2)" @mouseup="ptzCamera(0, 0, 0)"></i>
          </div>
          <div class="control-speed">
            <el-slider v-model="controSpeed" :max="255"></el-slider>
          </div>
        </div>
      </el-col>
      <el-col :span="20" style="height: 100%">
        <div class="groupButton">
          <div class="groupItem">
            <el-tag size="medium" type="info">预置位编号</el-tag>
            <el-input-number size="mini"
                             v-model="presetPos" controls-position="right" :precision="0" :step="1" :min="1"
                             :max="255"></el-input-number>
            <el-button size="mini" icon="el-icon-add-location" @click="presetPosition(129, presetPos)">设置</el-button>
            <el-button size="mini" type="primary" icon="el-icon-place" @click="presetPosition(130, presetPos)">调用</el-button>
            <el-button size="mini" icon="el-icon-delete-location" @click="presetPosition(131, presetPos)">删除</el-button>
          </div>
          <div class="groupItem">
            <el-tag size="medium" type="info">巡航速度</el-tag>
            <el-input-number size="mini" v-model="cruisingSpeed" controls-position="right" :precision="0" :min="1" :max="4095"></el-input-number>
            <el-button size="mini" icon="el-icon-loading" @click="setSpeedOrTime(134, cruisingGroup, cruisingSpeed)">设置</el-button>
            <el-tag size="medium" type="info">停留时间</el-tag>
            <el-input-number size="mini" v-model="cruisingTime" controls-position="right" :precision="0" :min="1" :max="4095"></el-input-number>
            <el-button size="mini" icon="el-icon-timer" @click="setSpeedOrTime(135, cruisingGroup, cruisingTime)">设置</el-button>
          </div>
          <div class="groupItem">
            <el-tag size="medium" type="info">巡航组编号</el-tag>
            <el-input-number size="mini" v-model="cruisingGroup" controls-position="right" :precision="0" :min="0" :max="255"></el-input-number>
            <el-button size="mini" icon="el-icon-add-location" @click="setCommand(132, cruisingGroup, presetPos)">添加点</el-button>
            <el-button size="mini" icon="el-icon-delete-location" @click="setCommand(133, cruisingGroup, presetPos)">删除点</el-button>
            <el-button size="mini" icon="el-icon-delete" @click="setCommand(133, cruisingGroup, 0)">删除组</el-button>
            <el-button size="mini" type="primary" icon="el-icon-video-camera-solid" @click="setCommand(136, cruisingGroup, 0)">巡航</el-button>
          </div>
          <div class="groupItem">
            <el-tag size="medium" type="info">扫描速度</el-tag>
            <el-input-number size="mini" v-model="scanSpeed" controls-position="right" :precision="0" :min="1" :max="4095"></el-input-number>
            <el-button size="mini" icon="el-icon-loading" @click="setSpeedOrTime(138, scanGroup, scanSpeed)">设置</el-button>
          </div>
          <div class="groupItem">
            <el-tag size="medium" type="info">扫描组编号</el-tag>
            <el-input-number size="mini" v-model="scanGroup" controls-position="right" :precision="0" :step="1" :min="0" :max="255"></el-input-number>
            <el-button size="mini" icon="el-icon-d-arrow-left" @click="setCommand(137, scanGroup, 1)">左边界</el-button>
            <el-button size="mini" icon="el-icon-d-arrow-right" @click="setCommand(137, scanGroup, 2)">右边界</el-button>
            <el-button size="mini" type="primary" icon="el-icon-video-camera-solid" @click="setCommand(137, scanGroup, 0)">扫描</el-button>
            <el-button size="mini" type="danger" icon="el-icon-switch-button" @click="ptzCamera(0, 0, 0)">停止</el-button>
          </div>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
  export default {
    name: "index",
    data() {
      return {
        controSpeed: '',
        presetPos: '',
        cruisingSpeed: '',
        cruisingTime: '',
        cruisingGroup: '',
        scanSpeed: '',
        scanGroup: '',
      }
    },
    methods: {
      presetPosition: function (cmdCode, presetPos) {

      },
      setSpeedOrTime: function (cmdCode, groupNum, parameter) {

      },
      setCommand: function (cmdCode, groupNum, parameter) {

      },
      ptzCamera: function (leftRight, upDown, zoom) {
        console.log('云台控制：' + leftRight + ' : ' + upDown + " : " + zoom);
        // 请求接口
      },
    }
  }
</script>

<style scoped lang="scss">
  .control-panel {
    height: 100%;
    margin-top: 15px;
  }
  .groupButton{
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    box-sizing: border-box;
    .groupItem{
      margin-bottom: 10px;
      .el-tag{
        min-width: 100px;
        text-align: center;
      }
    }
  }
  .control-zoom{
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 0 10px;
    box-sizing: border-box;
    .control-speed{
      width: 100%;
      margin-top: 15px;
    }
  }
  .control-zoom-btn {
    color: white;
    font-size: 38px;
    margin: 0 10px;
    &:hover{
      cursor: pointer
    }
  }
</style>
