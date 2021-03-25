<template>
  <div class="control-wrapper">
    <div class="control-btn control-top" @mousedown="ptzCamera(0, 2, 0)" @mouseup="ptzCamera(0, 0, 0)">
      <i class="el-icon-caret-top"></i>
      <div class="control-inner-btn control-inner"></div>
    </div>
    <div class="control-btn control-left" @mousedown="ptzCamera(2, 0, 0)" @mouseup="ptzCamera(0, 0, 0)">
      <i class="el-icon-caret-left"></i>
      <div class="control-inner-btn control-inner"></div>
    </div>
    <div class="control-btn control-bottom" @mousedown="ptzCamera(0, 1, 0)" @mouseup="ptzCamera(0, 0, 0)">
      <i class="el-icon-caret-bottom"></i>
      <div class="control-inner-btn control-inner"></div>
    </div>
    <div class="control-btn control-right" @mousedown="ptzCamera(1, 0, 0)" @mouseup="ptzCamera(0, 0, 0)">
      <i class="el-icon-caret-right"></i>
      <div class="control-inner-btn control-inner"></div>
    </div>
    <div class="control-round">
      <div class="control-round-inner"><i class="fa fa-pause-circle"></i></div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "index",
    methods: {
      ptzCamera: function (leftRight, upDown, zoom) {
        console.log('云台控制：' + leftRight + ' : ' + upDown + " : " + zoom);
        // 请求接口
      },
    }
  }
</script>

<style scoped lang="scss">
  .control-wrapper {
    position: relative;
    width: 8.25rem;
    height: 8.25rem;
    max-width: 8.25rem;
    max-height: 8.25rem;
  }
  .control-btn {
    display: flex;
    justify-content: center;
    position: absolute;
    width: 44%;
    height: 44%;
    border-radius: 5px;
    border: 1px solid #78aee4;
    box-sizing: border-box;
    transition: all 0.3s linear;
  }
  .control-btn:hover {
    cursor: pointer
  }
  .control-btn i {
    font-size: 20px;
    color: #78aee4;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .control-btn i:hover {
    cursor: pointer
  }
  .control-round {
    position: absolute;
    top: 21%;
    left: 21%;
    width: 58%;
    height: 58%;
    background: #fff;
    border-radius: 100%;
  }
  .control-round-inner {
    position: absolute;
    left: 13%;
    top: 13%;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 70%;
    height: 70%;
    font-size: 40px;
    color: #78aee4;
    border: 1px solid #78aee4;
    border-radius: 100%;
    transition: all 0.3s linear;
  }
  .control-inner-btn {
    position: absolute;
    width: 60%;
    height: 60%;
    background: #fafafa;
  }
  .control-top {
    top: -8%;
    left: 27%;
    transform: rotate(-45deg);
    border-radius: 5px 100% 5px 0;
  }
  .control-top i {
    transform: rotate(45deg);
    border-radius: 5px 100% 5px 0;
  }
  .control-top .control-inner {
    left: -1px;
    bottom: 0;
    border-top: 1px solid #78aee4;
    border-right: 1px solid #78aee4;
    border-radius: 0 100% 0 0;
  }
  .control-top .fa {
    transform: rotate(45deg) translateY(-7px);
  }
  .control-left {
    top: 27%;
    left: -8%;
    transform: rotate(45deg);
    border-radius: 5px 0 5px 100%;
  }
  .control-left i {
    transform: rotate(-45deg);
  }
  .control-left .control-inner {
    right: -1px;
    top: -1px;
    border-bottom: 1px solid #78aee4;
    border-left: 1px solid #78aee4;
    border-radius: 0 0 0 100%;
  }
  .control-left .fa {
    transform: rotate(-45deg) translateX(-7px);
  }
  .control-right {
    top: 27%;
    right: -8%;
    transform: rotate(45deg);
    border-radius: 5px 100% 5px 0;
  }
  .control-right i {
    transform: rotate(-45deg);
  }
  .control-right .control-inner {
    left: -1px;
    bottom: -1px;
    border-top: 1px solid #78aee4;
    border-right: 1px solid #78aee4;
    border-radius: 0 100% 0 0;
  }
  .control-right .fa {
    transform: rotate(-45deg) translateX(7px);
  }
  .control-bottom {
    left: 27%;
    bottom: -8%;
    transform: rotate(45deg);
    border-radius: 0 5px 100% 5px;
  }
  .control-bottom i {
    transform: rotate(-45deg);
  }
  .control-bottom .control-inner {
    top: -1px;
    left: -1px;
    border-bottom: 1px solid #78aee4;
    border-right: 1px solid #78aee4;
    border-radius: 0 0 100% 0;
  }
  .control-bottom .fa {
    transform: rotate(-45deg) translateY(7px);
  }
</style>
