<template>
  <button
    class="do-button"
    :class="{
      'is-loading': loading,
      [`do-button__${type}`]: type,
      'is-error': error
    }"
    @click="$emit('click')"
  >
    <svg v-if="icon && !loading" :class="{ [`do-icon-${icon}`]: icon }" aria-hidden="true">
      <use :xlink:href="`#icon-${icon}`" />
    </svg>
    <!-- <svg v-if="loading" class="do-icon-loading" aria-hidden="true">
      <use xlink:href="#icon-spinner" />
    </svg> -->
    <LoadingIcon v-if="loading" type="all" />
    <span class="do-button__content">
      <slot />
    </span>
  </button>
</template>
<script>
import LoadingIcon from './LoadingIcon.vue'
export default {
  name: 'DoButton',
  components: { LoadingIcon },
  props: {
    // bright: {
    //   type: Boolean,
    //   default: false
    // },
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
        return value === 'default' || value === 'primary'
      }
    },
    error: {
      type: Boolean,
      default: false
    }
  }
}
</script>
<style lang="scss" src="../styles/button.scss"></style>
