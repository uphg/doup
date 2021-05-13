<template>
  <div class="do-button-group">
    <slot />
  </div>
</template>
<script>
export default {
  name: 'DoButtonGroup',
  mounted() {
    if (this.$el.children.length < 1) {
      console.error('Do: do-button must exist in do-button-group!')
    }
    for (const el of this.$el.children) {
      const name = el.nodeName.toLowerCase()
      if (name !== 'button') console.warn(`Do: The child element of do-button-group should be do-button, not ${name}.`)
    }
  }
}
</script>
<style lang="scss" src="../styles/button-group.scss"></style>
