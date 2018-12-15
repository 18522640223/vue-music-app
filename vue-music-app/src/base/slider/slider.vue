<template>
    <div class="slider">
        <div class="slider-group">
            <slot></slot>
        </div>
    </div>
</template>
<script>
export default {
  props: {
    loop: {
      type: Boolean,
      default: true
    },
    autoPlay: {
      type: Boolean,
      default: true
    },
    interval: {
      type: Number,
      default: 4000
    }
  },
  mounted () {
    setTimeout(() => {
      this._setSliderWidth()
      this._initSilder()
    }, 20)
  },
  methods: {
    _setSliderWidth () {},
    _initSilder () {}
  }
}
</script>
<style lang="stylus" scoped>
@import '~common/stylus/variable'
</style>
