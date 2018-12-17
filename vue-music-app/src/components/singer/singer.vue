<template>
  <div class="singer-content">
    <singer-list v-if="singerList.length">
      <cube-index-list :data="singerList"></cube-index-list>
    </singer-list>
  </div>
</template>
<script>
import { getSingerList, ERR_OK } from 'api/singer.js'
import SingerList from 'base/singerList/singerList.vue'
const HOT_NAME = '热门'
const HOT_SINGER_LENGTH = 10
export default {
  data () {
    return {
      singerList: []
    }
  },
  components: {
    SingerList
  },
  methods: {
    _getSingerList () {
      getSingerList().then((res) => {
        if (ERR_OK === res.data.code) {
          console.log(res.data.data.list)
          this._initSingerList(res.data.data.list)
        }
      })
    },
    _initSingerList (list) {
      let map = {
        name: HOT_NAME,
        items: []
      }
      list.forEach((item, index) => {
        if (index < HOT_SINGER_LENGTH) {
          map.items.push({
            name: item.Fsinger_name,
            value: item.Fsinger_mid
          })
        }
      })
      console.log(map)
      this.singerList.push(map)
    }
  },
  created () {
    this._getSingerList()
  }
}
</script>
<style lang="stylus" scoped>
</style>
