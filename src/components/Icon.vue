
<template>
  <svg :class="{ [`do-icon-${name}`]: name }" aria-hidden="true">
    <use :xlink:href="iconName" />
  </svg>
</template>

<script>
export default {
  name: 'DoIcon',
  props: {
    name: {
      type: String,
      required: true
    }
  },
  computed: {
    iconName() {
      return `#icon-${this.name}`
    }
  }
}
</script>
<style lang="scss" src="../styles/icon.scss"></style>
