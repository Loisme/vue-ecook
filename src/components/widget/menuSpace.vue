<template>
  <div @click="gotoMenuDetail">
    <img class="img-card" :src="getImageUrl(menuArr.imageid)"/>
    <div class="title">{{menuArr.name}}</div>
    <div class="name">{{menuArr.user.nickname}}</div>
  </div>
</template>

<script>
  import menuBase from './menuBase.vue';

  export default {
    name: 'menuSpace',
    extends: menuBase,
  };
</script>

<style scoped>
  .img-card {
    width: 100%;
    height: 8rem;
    border-radius: 5px;
    box-shadow: 5px 5px 5px #dddddd;
    border: 1px solid #dddddd;
  }

  .title {
    width: 100%;
    margin: 10px 0 0 0;
    font-size: 14pt;
    font-weight: bold;
    color: black;
    white-space: nowrap; /* 不换行 */
    overflow: hidden; /* 内容超出宽度时隐藏超出部分的内容 */
    text-overflow: ellipsis; /* 当对象内文本溢出时显示省略标记(...) ；需与overflow:hidden;一起使用。*/
  }

  .name {
    width: 100%;
    margin: 10px 0 10px 0;
    font-size: 12pt;
  }
</style>
