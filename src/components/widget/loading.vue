<template>
  <div class="loading" v-show="show">
    <div class="loader-inner ball-pulse">
      <div></div>
      <div></div>
      <div></div>
    </div>
  </div>
</template>
<script>
  export default {
    name: 'v-loading',
    props: {
      show: {
        type: Boolean
      }
    }
  };
</script>

<style>
  .loading {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 30;
    width: 100%;
    height: 100%;
    background-color: #ffffff;
    opacity: 0.4;
  }

  .ball-pulse {
    position: absolute;
    top: 50%;
    left: 45%;
  }

  .ball-pulse div {
    background-color: orange;
    width: 15px;
    height: 15px;
    border-radius: 100%;
    margin: 2px;
    animation-fill-mode: both;
    display: inline-block;
  }

  .ball-pulse > div:nth-child(1) {
    animation: scale 0.75s -0.24s infinite cubic-bezier(0.2, 0.68, 0.18, 1.08);
  }

  .ball-pulse > div:nth-child(2) {
    animation: scale 0.75s -0.12s infinite cubic-bezier(0.2, 0.68, 0.18, 1.08);
  }

  .ball-pulse > div:nth-child(3) {
    animation: scale 0.75s 0s infinite cubic-bezier(0.2, 0.68, 0.18, 1.08)
  }

  @-webkit-keyframes scale {
    0% {
      -webkit-transform: scale(1);
      transform: scale(1);
      opacity: 1;
    }
    45% {
      -webkit-transform: scale(0.1);
      transform: scale(0.1);
      opacity: 0.7;
    }
    80% {
      -webkit-transform: scale(1);
      transform: scale(1);
      opacity: 1;
    }
  }

  @keyframes scale {
    0% {
      -webkit-transform: scale(1);
      transform: scale(1);
      opacity: 1;
    }
    45% {
      -webkit-transform: scale(0.1);
      transform: scale(0.1);
      opacity: 0.7;
    }
    80% {
      -webkit-transform: scale(1);
      transform: scale(1);
      opacity: 1;
    }
  }
</style>
