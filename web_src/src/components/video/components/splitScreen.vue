<template>
  <div class="splitView">
    <el-row class="splitFull">
      <el-col :span="12" style="height: 100%">
        <el-row class="splitHalf">
          <el-col class="splitFull">
            <player ref="videoPlayer"
                    :videoUrl="videoUrl"
                    :error="videoError"
                    :message="videoError"
                    fluent autoplay live/>
          </el-col>
        </el-row>
        <el-row class="splitHalf">
          <table class="splitTable">
            <tr>
              <td>
                <player
                  ref="fourOnePlayer"
                  :videoUrl="videoUrl"
                  :error="videoError"
                  :message="videoError"
                  fluent autoplay live/>
              </td>
              <td>
                <player
                  ref="fourTwoPlayer"
                  :videoUrl="videoUrl"
                  :error="videoError"
                  :message="videoError"
                  fluent autoplay live/>
              </td>
            </tr>
            <tr>
              <td>
                <player
                  ref="fourThreePlayer"
                  :videoUrl="videoUrl"
                  :error="videoError"
                  :message="videoError"
                  fluent autoplay live/>
              </td>
              <td>
                <player
                  ref="fourFourPlayer"
                  :videoUrl="videoUrl"
                  :error="videoError"
                  :message="videoError"
                  fluent autoplay live/>
              </td>
            </tr>
          </table>
        </el-row>
      </el-col>
      <el-col :span="12" style="height: 100%">
        <table class="splitTable">
          <tr>
            <td>
              <player
                ref="nine1Player"
                :videoUrl="videoUrl"
                :error="videoError"
                :message="videoError"
                fluent autoplay live/>
            </td>
            <td>
              <player
                ref="nine2Player"
                :videoUrl="videoUrl"
                :error="videoError"
                :message="videoError"
                fluent autoplay live/>
            </td>
            <td>
              <player
                ref="nine3Player"
                :videoUrl="videoUrl"
                :error="videoError"
                :message="videoError"
                fluent autoplay live/>
            </td>
          </tr>
          <tr>
            <td>
              <player
                ref="nine4Player"
                :videoUrl="videoUrl"
                :error="videoError"
                :message="videoError"
                fluent autoplay live/>
            </td>
            <td>
              <player
                ref="nine5Player"
                :videoUrl="videoUrl"
                :error="videoError"
                :message="videoError"
                fluent autoplay live/>
            </td>
            <td>
              <player
                ref="nine6Player"
                :videoUrl="videoUrl"
                :error="videoError"
                :message="videoError"
                fluent autoplay live/>
            </td>
          </tr>
          <tr>
            <td>
              <player
                ref="nine7Player"
                :videoUrl="videoUrl"
                :error="videoError"
                :message="videoError"
                fluent autoplay live/>
            </td>
            <td>
              <player
                ref="nine8Player"
                :videoUrl="videoUrl"
                :error="videoError"
                :message="videoError"
                fluent autoplay live/>
            </td>
            <td>
              <player
                ref="nine9Player"
                :videoUrl="videoUrl"
                :error="videoError"
                :message="videoError"
                fluent autoplay live/>
            </td>
          </tr>
        </table>
      </el-col>
    </el-row>
  </div>
</template>

<script>
  import Player from '../player'
  export default {
    name: "index",
    components: {
      Player
    },
    data() {
      return {
        videoUrl: 'http://ivi.bupt.edu.cn/hls/cctv1hd.m3u8',
      }
    },
    mounted() {
      this.$nextTick(() => {
        this.$refs.videoPlayer.play(this.videoUrl)
        this.$refs.fourOnePlayer.play(this.videoUrl)
        this.$refs.fourTwoPlayer.play(this.videoUrl)
        this.$refs.fourThreePlayer.play(this.videoUrl)
        this.$refs.fourThreePlayer.play(this.videoUrl)
        this.$refs.nine1Player.play(this.videoUrl)
        this.$refs.nine2Player.play(this.videoUrl)
        this.$refs.nine3Player.play(this.videoUrl)
        this.$refs.nine4Player.play(this.videoUrl)
        this.$refs.nine5Player.play(this.videoUrl)
        this.$refs.nine6Player.play(this.videoUrl)
        this.$refs.nine7Player.play(this.videoUrl)
        this.$refs.nine8Player.play(this.videoUrl)
        this.$refs.nine9Player.play(this.videoUrl)
      })
    },
    methods: {
      videoError(e) {
        console.log("播放器错误：" + JSON.stringify(e));
      },
    }
  }
</script>

<style lang="scss">
  .splitView{
    width: 100%;
    height: 100%;
  }
  .splitFull{
    width: 100%;
    height: 100%
  }
  .splitHalf{
    width: 100%;
    height: 50%;
  }
  .splitTable{
    width: 100%;
    height: 100%;
    border-collapse: collapse;
    table-layout: fixed;
    td{
      position: relative;
    }
  }
</style>
