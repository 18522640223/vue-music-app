<template>
    <div class="rank-content">
        我是排行页
        <loading :flg="flg"></loading>
    </div>
</template>
<script>
import { getRank, ERR_OK } from 'api/rank.js'
import Loading from 'base/loading/loading.vue'
export default {
  data () {
    return {
      flg: false
    }
  },
  created () {
    this._getRanks()
  },
  methods: {
    _getRanks () {
      this.flg = true
      getRank().then((res) => {
        if (res.data.code === ERR_OK) {
          this.flg = false
          console.log(res.data.data)
        }
      })
    }
  },
  components: {
    Loading
  }
}
</script>
<style lang="stylus" scoped></style>
