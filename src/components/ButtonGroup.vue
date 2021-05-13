<template>
  <div class="do-button-group">
    <slot />
  </div>
</template>
<script>
export default {
  name: 'DoButtonGroup'
}
</script>
<style lang="scss">
.do-button-group {
  display: inline-flex;
  vertical-align: middle;
}
</style>
