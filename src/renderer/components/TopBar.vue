<template>
  <div class="top-bar">
    <i class="logo"></i>
    <i class="left-arrow"></i>
    <i class="right-arrow"></i>
    <div class="search-box">
      <input type="text">
      <i class="search"></i>
    </div>
  </div>
</template>
<script>
  export default {
    name: 'top-bar',
    components: {},
    methods: {
      open(link) {
        this.$electron.shell.openExternal(link);
      }
    }
  };
</script>
<style lang="scss">
.top-bar {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 60px;
  background-color: #C20C0C;
  display: flex;
  align-items: center;
  .logo {
    display: inline-block;
    width: 200px;
    height: 60px;
    background: url('../assets/topbar.png') no-repeat 0 0;
  }
  .left-arrow {
    display: inline-block;
  }
  .right-arrow {
    display: inline-block;
  }
  .search-box {
    display: inline-block;
    width: 270px;
    height: 28px;
    color: rgb(197, 109, 109);
    background-color: rgb(168, 40, 40);
    border-radius: 28px;
    padding: 5px 10px;
    input {
      outline: none;
      -webkit-appearance: none;
      border: none;
      background: transparent;
    }
    .search {
      display: inline-block;
      background: url('../assets/topbar.png') no-repeat 0 -99px;
    }
  }
}
</style>
