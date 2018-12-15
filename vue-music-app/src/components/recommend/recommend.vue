<template>
  <div class="recommend">
    <slider>
      <cube-slide>
        <cube-slide-item
          v-if="recommends.length"
          v-for="(item, index) in recommends"
          :key="index"
        >
          <a :href="item.linkUrl">
            <img :src="item.picUrl">
          </a>
        </cube-slide-item>
      </cube-slide>
    </slider>
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
</style>
