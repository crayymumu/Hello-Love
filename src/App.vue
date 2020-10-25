<template>
  <div id="app">
    <div ref="app-container" class="app-container">
      <template v-if="pass">
        <music-btn class="music-btn" />
        <router-view />
      </template>
      <div v-else class="input-container">
        <div>
          <wired-input ref="birthdayInput" placeholder="Please enter birthday" />
          <wired-button @click="handleCheck">
            确认
          </wired-button>
        </div>
      </div>
      <wired-dialog :open="dialogDisplay">
        <p>
          错了哦~ 答案很明显呢
        </p>
      </wired-dialog>
    </div>
    <loading />
  </div>
</template>
<script>
import MusicBtn from '@/components/MusicBtn'
import Loading from '@/components/Loading'
import { initCanvas } from '@/utils/canvas'
import WiredInput from 'wired-input'
import WiredButton from 'wired-button'
import WiredDialog from 'wired-dialog'
import md5 from 'blueimp-md5'

export default {
  components: {
    MusicBtn,
    Loading,
    WiredInput,
    WiredButton,
    WiredDialog,
  },
  data() {
    return {
      pass: false,
      dialogDisplay: false
    }
  },
  mounted() {
    initCanvas(this.$refs['app-container'])
  },
  methods: {
    handleCheck() {
      const passwordAdd = md5(this.$refs.birthdayInput.value)
      if (passwordAdd === 'cf673f7ee88828c9fb8f6acf2cb08403') {
        this.pass = true
      } else {
        this.dialogDisplay = true
        setTimeout(() => {
          this.dialogDisplay = false
        }, 2000)
      }
    }
  }
}
</script>
<style lang="scss">
html,
body,
#app,
.app-container {
  width: 100%;
  height: 100%;

  .rough-canvas {
    position: absolute;
    top: 0;
    left: 0;
    z-index: -1;
  }
  .input-container {
    width: 100%;
    height: 100%;
    display: flex;
    align-items:center;
    justify-content:center;
  }
}
</style>
