<template>
    <div class="ybb-swipe-box" id="ybb-swipe-box">
        <mt-swipe :auto="4000">
          <mt-swipe-item v-for="item in items">
            <router-link :to="{name:'SwipeInfo', params: {id:item.id}}" v-show="item.releaseType===2">
              <img v-lazy="makePhotoUrl(item.titlePic)"  class="page-lazyload-image">
            </router-link><!-- v-lazy="item.imgUrl" -->
            <a :href="item.activityUrl" target="_blank" v-show="item.releaseType===1">
              <img v-lazy="makePhotoUrl(item.titlePic)" class="page-lazyload-image">
            </a>
          </mt-swipe-item>
        </mt-swipe>
    </div>
</template>

<script>
import helpers from '../../utils/helpers'
export default {
  props: {
    items: {
      type: Array,
      required: true
    }
  },
  methods: {
    makePhotoUrl: function (url) {
      // 返回的数据中 多了‘|’ 所以去除
      var photoUrl = url ? helpers.makePhotoUrl(url.replace('|', '')) : ''
      // console.info('loading image:' + photoUrl)
      return photoUrl
    }
  }
}
</script>
<style scoped>
.ybb-swipe-box img {
  height: 100%;
}
</style>
