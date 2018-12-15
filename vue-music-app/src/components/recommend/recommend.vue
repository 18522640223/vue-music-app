<template>
  <div class="recommend">
    <slider v-if="recommends.length">
      <cube-slide>
        <cube-slide-item
          v-for="(item, index) in recommends"
          :key="index"
        >
          <a :href="item.linkUrl">
            <img :src="item.picUrl">
          </a>
        </cube-slide-item>
      </cube-slide>
    </slider>
    <div class="recommend-list">
      <h1 class="list-title">热门歌单推荐</h1>
    </div>
  </div>
</template>
<script>
import { getRecommend, ERR_OK } from 'api/recommend.js'
import Slider from 'base/slider/slider.vue'
export default {
  data () {
    return {
      recommends: [],
      options: {}
    }
  },
  created () {
    this._getRecommend()
  },
  components: {
    Slider
  },
  methods: {
    _getRecommend () {
      getRecommend().then((res) => {
        if (res.code === ERR_OK) {
          this.recommends = res.data.slider
        }
        console.log(res)
      })
    }
  }
}
</script>
<style lang="stylus" scoped>
@import '~common/stylus/variable'
  .slider-group
    img
      width: 100%
  .recommend-list
    .list-title
      height: 65px
      line-height: 65px
      text-align: center
      font-size: $font-size-medium
      color: $color-theme
</style>
