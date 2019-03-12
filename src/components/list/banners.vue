<template>
  <div class="swiper-div">
    <swiper ref="swiper" v-if="list.length>0">
      <div class="wh_slide" v-for="(item,index) in list" :key=index @click="gotoCollection(item.url)">
        <img class="img-main" :src="getImageUrl(item.image)"/>

<!--        <div class="img-data">
          <img class="img-bg blur" :src="getImageUrl(item.image)"/>
        </div>-->
      </div>
    </swiper>
  </div>
</template>
<script>
  import swiper from '../widget/slider.vue';

  export default {
    props: {
      list: {
        type: Array
      }
    },
    methods: {
      getImageUrl(imageId) {
        return `http://pic.ecook.cn/web/${imageId}.jpg!m4`;
      },
      gotoCollection(url) {
        let id = this.getCollectionId(url);
        this.$router.push({name: 'collectionSort', query: {id: id}});
      },
      getCollectionId(url) {  // 获取url参数
        const vars = url.split("?"); // 分割符
        for (let i = 0; i < vars.length; i++) {
          const pair = vars[i].split("=");
          if (pair[0] === "id") {
            return pair[1];
          }
        }
        return false;
      }
    },
    components: {
      swiper,
    }
  };
</script>
<style>
  .swiper-div {
    width: 100%;
    height: 30vh;
  }

  .img-data {
    position: relative;
  }

  .img-main {
    text-align: center;
    width: 100%;
    height: 30vh;
    z-index: 99;
  }

  .img-bg {
    text-align: center;
    width: 100%;
    height: 30vh;
  }

  .blur {
    -webkit-filter: blur(10px);
    -moz-filter: blur(10px);
    -ms-filter: blur(10px);
    filter: blur(10px);
  }

  .wh_slide {
    width: 100%;
    min-height: 100px;
    -ms-flex-negative: 0;
    flex-shrink: 0;
    z-index: 10;
  }
</style>
