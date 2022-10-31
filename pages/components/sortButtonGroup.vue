<template>
  <view class="f fjsb h100">
    <slot></slot> 
  </view>
</template>

<script>
export default {
  name: 'SortButtonGroup',
  componentName: 'SortButtonGroup',
  model: {
    event: 'change'
  },
  props: {
    value: {
      type: Object,
      default: () => { return {} }
    }
  }
}
</script>

<style lang="scss" scoped>
.h100 {
  height: 100%;
}
</style>
