<template>
  <div id="app">
    <top-bar></top-bar>
    <left-bar></left-bar>
    <bottom-bar></bottom-bar>
    <main></main>
    <!-- <router-view></router-view> -->
  </div>
</template>

<script>
  import leftBar from './components/LeftBar';
  import topBar from './components/TopBar';
  import bottomBar from './components/BottomBar';
  import main from './components/Main';
  export default {
    name: 'netease-cloud-music',
    components: {
      bottomBar,
      leftBar,
      topBar,
      main
    }
  };
</script>

<style>
  @import './assets/css/reset';
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
