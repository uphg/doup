<template>
  <div id="app">
    <h2>按钮</h2>
    <div class="row">
      <span class="label">普通按钮：</span>
      <do-button>默认按钮</do-button>
      <do-button type="primary">主要按钮</do-button>
      <do-button type="error">警告按钮</do-button>
    </div>
    <div class="row">
      <span class="label">Icon 按钮：</span>
      <do-button icon="bug">主要按钮</do-button>
      <do-button type="primary" icon="bug">默认按钮</do-button>
      <do-button type="error" icon="bug">警告按钮</do-button>
    </div>
    <div class="row">
      <span class="label">Loading 按钮：</span>
      <do-button :loading="isLoading" @click="isLoading = !isLoading">默认按钮</do-button>
      <do-button type="primary" :loading="isLoading" @click="isLoading = !isLoading">主要按钮</do-button>
      <do-button type="error" :loading="isLoading" @click="isLoading = !isLoading">警告按钮</do-button>
    </div>
    <h2>倒计时</h2>
    <div class="row">
      <span class="label">倒计时按钮：</span>
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
      <span class="label">Icon 组件：</span>
      <do-icon name="alarm" />
      <do-icon name="aspect-ratio" />
    </div>
    <h2>按钮组</h2>
    <div class="row button-group">
      <do-button-group style="margin-right: 20px; margin-">
        <do-button>上一页</do-button>
        <do-button>当前页</do-button>
        <do-button>下一页</do-button>
      </do-button-group>
      <do-button-group>
        <do-button type="primary">上一页</do-button>
        <do-button type="primary">当前页</do-button>
        <do-button type="primary">下一页</do-button>
      </do-button-group>
      <do-button-group>
        <do-button type="error">上一页</do-button>
        <do-button type="error">当前页</do-button>
        <do-button type="error">下一页</do-button>
      </do-button-group>
    </div>
  </div>
</template>

<script>
import Button from './components/Button.vue'
import ButtonGroup from './components/ButtonGroup.vue'
import Countdown from './components/Countdown.vue'
import Icon from './components/Icon.vue'

export default {
  name: 'App',
  components: {
    DoButton: Button,
    DoButtonGroup: ButtonGroup,
    DoCountdown: Countdown,
    DoIcon: Icon
  },
  data() {
    return {
      isLoading: false,
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
h2 {
  text-align: center;
}

.row {
  margin: {
    top: 20px;
    bottom: 20px;
  }
  &:not(.button-group) {
    button {
      margin-right: 15px;
    }
  }
}
.icon-list > [class^="do-icon-"] {
  margin-right: 20px;
}
.label {
  text-align: right;
  width: 120px;
  display: inline-block;
  padding-right: 10px;
}
</style>
