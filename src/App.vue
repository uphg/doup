<template>
  <div id="app">
    <h2>按钮</h2>
    <div class="row">
      <do-button>主要按钮</do-button>
    </div>
    <div class="row">
      <do-button icon="bug">ICON按钮</do-button>
    </div>
    <div class="row">
      <do-button :loading="true">Loading按钮</do-button>
    </div>
    <h2>倒计时</h2>
    <div class="row">
      <do-countdown
        ref="countdown"
        :count="5"
        @count-open="isCount = true"
        @count-end="isCount = false"
        @click="clickCount"
      />
    </div>
    <h2>Icon 图标</h2>
    <div class="row icon-list">
      <do-icon name="alarm" />
      <do-icon name="aspect-ratio" />
    </div>
  </div>
</template>

<script>
import Button from './components/Button.vue'
import Countdown from './components/Countdown.vue'
import Icon from './components/Icon.vue'

export default {
  name: 'App',
  components: {
    DoButton: Button,
    DoCountdown: Countdown,
    DoIcon: Icon
  },
  data() {
    return {
      isCount: false
    }
  },
  methods: {
    clickCount() {
      if (!this.isCount) {
        console.log('开启倒计时')
        this.$refs['countdown'].startCount()
      }
    }
  }
}
</script>

<style lang="scss">
#app {
  width: 670px;
  margin: 0 auto;
  padding: {
    left: 20px;
    right: 20px;
  }
}
.row {
  margin: {
    top: 20px;
    bottom: 20px;
  }
}
.icon-list > .do-icon {
  margin-right: 20px;
}
</style>
