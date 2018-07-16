<template>
  <div id="app">
    <top-bar></top-bar>
    <left-bar></left-bar>
    <bottom-bar></bottom-bar>
    <main-block></main-block>
    <!-- <router-view></router-view> -->
  </div>
</template>

<script>
  import leftBar from './components/LeftBar';
  import topBar from './components/TopBar';
  import bottomBar from './components/BottomBar';
  import mainBlock from './components/MainBlock';
  export default {
    name: 'netease-cloud-music',
    components: {
      bottomBar,
      leftBar,
      topBar,
      mainBlock
    }
  };
</script>

<style>
  @import './assets/css/reset';
  @import './assets/css/index';
  html, body {
    width: 100%;
    height: 100%;
    min-width: 1277px;
    min-height: 837px;
  }
  #app {
    width: 100%;
    height: 100%;
  }
</style>
