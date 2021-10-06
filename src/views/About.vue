<template>
  <div class="about">
    <button @click="getWangyi">获取热门歌单</button>
    {{this.a}}
  </div>
</template>

<script>
import axios from '@/plugins/axios.js' /* 引入封装的axios */

export default {
  // eslint-disable-next-line @typescript-eslint/explicit-module-boundary-types
  data () {
    return {
      a: ''
    }
  },
  methods: {
    // eslint-disable-next-line @typescript-eslint/explicit-module-boundary-types
    getWangyi () {
      axios({
        url: '/playlist/hot', /* 热门歌单接口地址 */
        method: 'post'
      })
        .then(res => {
          console.log('我拿到的数据：', res.data.tags)
          this.a = res.data.tags
        })
        .catch(err => {
          console.log(err)
        })
    }
  }
}
</script>
