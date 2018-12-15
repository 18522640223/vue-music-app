<template>
    <div>
        我是推荐页
    </div>
</template>
<script>
import { getRecommend } from '../../api/recommend.js'
export default {
  data () {
    return {
      data: ''
    }
  },
  created () {
    this._getRecommend()
  },
  methods: {
    _getRecommend () {
      getRecommend().then((res) => {
        console.log(res)
      })
    }
  }
}
</script>
<style lang="stylus" scoped></style>
