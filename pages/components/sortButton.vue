<template>
  <view class="f fac pointer">
    <view @click="onClickText">
      <slot></slot>
    </view>
    <view class="yz-icon-d-caret">
      <!-- class改成name -->
      <u-icon :color="upClass" name="arrow-up-fill" @click="onClickUp"></u-icon>
      <u-icon :color="downClass" name="arrow-down-fill" @click="onClickDown"></u-icon>
    </view>
  </view>
</template>

<script>
// import Emitter from 'element-ui/src/mixins/emitter'
export default {
  name: 'SortButton',
  // mixins: [Emitter],
  props: {
    value: {
      type: String,
      default: ''
    }
  },
  computed: {
    upClass () {

      if (this.$parent.$parent.value.value !== this.value) {
        return '#909399'
      }
      return this.$parent.$parent.value.sort === '1' ? '#fa3534' : '#909399' //1:升序，2：降序
    },
    downClass () {
      if (this.$parent.$parent.value.value !== this.value) {
        return '#909399'
      }
      return this.$parent.$parent.value.sort === '2' ? '#fa3534' : '#909399' //1:升序，2：降序
    }
  },
  methods: {
    onClickText() {
      console.log('onClickSlot');
      if (this.$parent.$parent.value.value !== this.value) {
        return this.onClickUp();
      }
      return this.$parent.$parent.value.sort === '1'
        ? this.onClickDown()
        : this.onClickUp(); //1:升序，2：降序
    },
    onClickUp () {
      this.$parent.$parent.$emit('change', { value: this.value, sort: '1' });
		},
    onClickDown () {
			this.$parent.$parent.$emit('change', { value: this.value, sort: '2' });
    }
  }
}
</script>
<style scoped>
::v-deep .u-icon {
  color: #8D8D8D;
}
</style>
<style lang="scss" scoped>
// .f {
//   display: flex;
// }
// .fac {
//   align-items: center;
// }
.pointer {
  cursor: pointer;
  user-select: none;
}
.yz-icon-d-caret {
  display: flex;
  flex-direction: column;
  // margin: 0 3px;
  width: 10px;
  u-icon {
    color: #8D8D8D;
  }
  .el-icon-caret-top{
    height: 7px;
  }
  .red {
    color: #F11111;
  }
}
</style>
