<template>
  <div>
    <div class="title-data">
      <div class="title-info">{{title}}</div>
      <div class="more" @click="gotoMoreData">更多></div>
    </div>
    <!-- 菜谱列表 -->
    <div class="page-content">
      <menu-data class="page-item" :menuArr="item" v-for="item in list"></menu-data>
    </div>
  </div>
</template>

<script>
  import menuData from '../widget/menuSpace.vue';

  export default {
    name: 'interest',
    props: {
      title: {
        type: String
      },
      list: {
        type: Array
      }
    },
    components: {
      menuData
    },
    methods: {
      gotoMoreData() {
        this.$router.push({name: 'recommend', query: {title: '菜谱推荐', type: 'latest'}});
      }
    }
  }
</script>

<style scoped>
  .title-data {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    margin: 25px 25px 10px 15px;
  }

  .title-info {
    font-weight: bold;
    font-size: 16pt;
    color: black;
  }

  .page-content {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-between;
    padding: 10px 15px;
  }

  .page-item {
    width: 45vw;
    flex: 0 0 auto;
    height: auto;
    padding-bottom: 15px;
  }
</style>
