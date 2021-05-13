<template>
  <button class="do-button" :class="{ 'is-loading': loading, [`do-button__${type}`]: type }" @click="$emit('click')">
    <svg v-if="icon && !loading" :class="{ [`do-icon-${icon}`]: icon }" aria-hidden="true">
      <use :xlink:href="`#icon-${icon}`" />
    </svg>
    <svg v-if="loading" class="do-icon-loading" aria-hidden="true">
      <use xlink:href="#icon-spinner" />
    </svg>
    <span class="do-button__content">
      <slot />
    </span>
  </button>
</template>
<script>
export default {
  name: 'DoButton',
  props: {
    icon: {
      type: String,
      default: ''
    },
    loading: {
      type: Boolean,
      default: false
    },
    type: {
      type: String,
      default: 'default',
      validator(value) {
        return value === 'primary' || 'default'
      }
    }
  }
}
</script>
<style lang="scss" src="../styles/button.scss"></style>
