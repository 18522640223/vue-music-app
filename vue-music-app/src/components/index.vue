<template>
  <div class="hello">
    <m-header></m-header>
    <tab></tab>
    2222
  </div>
</template>

<script>
import { getRecommend } from '../api/recommend.js'
import MHeader from '../components/m-header/m-header.vue'
import Tab from '../components/tab/tab.vue'
export default {
  name: 'HelloWorld',
  data () {
    return {}
  },
  created () {
    this._getRecommend()
  },
  components: {
    MHeader,
    Tab
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
