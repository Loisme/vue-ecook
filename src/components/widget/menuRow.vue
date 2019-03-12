<template>
  <div>
    <!-- 详情页链接 -->
    <router-link :to="{path:'/menuDetail',query: {id: menuArr.id, info: menuArr} }"
                 @click.native="addIntoHistory(menuArr)">

      <div class="menuRow">
        <img class="img-card" :src="getImageUrl(menuArr.imageid)"/>
        <div class="content">
          <div class="name text-wrapper">{{menuArr.name}}</div>
          <div class="desc text-wrapper">{{ menuArr.description}}</div>
          <div class="browse-info">
            <div class="favorite-count">{{ menuArr.infos.collectionCount }}人收藏</div>
            <div class="favorite-like">{{ menuArr.infos.likeCount }}人点赞</div>
          </div>
        </div>
      </div>

    </router-link>
  </div>
</template>

<script>
  import {addIntoHistoryList} from '../../common/js/localStorage';

  export default {
    name: 'menuRow',
    props: {
      menuArr: {
        type: Object
      }
    },
    methods: {
      getImageUrl: function (imageId) {
        return `http://pic.ecook.cn/web/${imageId}.jpg!s2`;
        // return `http://pic.ecook.cn/web/${imageId}.jpg!m4`;
      },
      addIntoHistory (menuArr) { // 添加浏览记录
        addIntoHistoryList(menuArr);
      }
    }
  };
</script>

<style scoped>

  .menuRow {
    display: flex;
    display: -webkit-flex;
    align-items: center;
    border-radius: 5px;
    box-shadow: 5px 5px 5px #dddddd;
    border: 1px solid #dddddd;
  }

  .img-card {
    max-width: 30%;
    max-height: 100%;
    border-radius: 5px 0 0 5px;
  }

  .content {
    display: flex;
    flex-direction: column;
    display: -webkit-flex;
    width: 100%;
    padding: 0 10px;
    overflow: hidden;
  }
  .name {
    flex: 1;
    align-self: flex-start;
    padding-top: 5px;
    font-size: 14pt;
    color: black;
  }

  .desc {
    flex: 2;
    padding-top: 10px;
    padding-bottom: 10px;
    color: gray;
    font-size: 12pt;
    overflow: hidden;
    text-overflow: ellipsis;
    /*white-space: nowrap;*/
  }

  .text-wrapper {
    width: 64vw;
    white-space: nowrap; /* 不换行 */
    overflow: hidden; /* 内容超出宽度时隐藏超出部分的内容 */
    text-overflow: ellipsis; /* 当对象内文本溢出时显示省略标记(...) ；需与overflow:hidden;一起使用。*/
  }

  .browse-info {
    flex: 1;
    display: flex;
    display: -webkit-flex;
    margin-right: 20px;
    padding-bottom: 5px;
    color: gray;
  }

  .favorite-count {
    font-size: 10pt;
  }

  .favorite-like {
    font-size: 10pt;
    margin-left: 10px;
  }
</style>
