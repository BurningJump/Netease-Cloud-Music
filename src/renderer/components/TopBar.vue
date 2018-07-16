<template>
  <div class="top-bar">
    <i class="logo"></i>
    <div class="history">
      <i class="icon left-arrow"></i>
      <i class="icon right-arrow"></i>
    </div>
    <div class="search-box">
      <input type="text">
      <i class="icon search"></i>
    </div>
    <div class="user">
      <img src="" alt="">
      <span class="username">{{username}}</span>
    </div>
    <div class="icons">
      <i class="icon theme"></i>
      <i class="icon email"></i>
      <i class="icon setting"></i>
    </div>
    <div class="handle">
      <i class="icon mini"></i>
      <i class="icon min"></i>
      <i class="icon max"></i>
      <i class="icon close"></i>
    </div>
  </div>
</template>
<script>
  export default {
    name: 'top-bar',
    data() {
      return {
        username: 'burningjump'
      };
    },
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
  .history {
    display: inline-flex;
    width: 65px;
    height: 24px;
    .left-arrow {
      width: 32px;
      height: 100%;
      border-right: 1px solid rgb(167, 39, 39);
    }
    .right-arrow {
      width: 32px;
      height: 100%;
      display: inline-block;
    }
  }
  .search-box {
    display: inline-flex;
    justify-content: center;
    align-items: center;
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
      width: 24px;
      height: 24px;
      background: url('../assets/topbar.png') no-repeat 0 -99px;
    }
  }
  .user {
    display: inline-flex;
    justify-content: center;
    align-items: center;
    img {
      display: inline-block;
      width: 30px;
      height: 30px;
      border-radius: 50%;
      background-color: blue;
    }
    .username {
      color: rgb(238, 193, 193);
    }
  }
  .icons {
    border-right: 1px solid rgb(168, 40, 40);
    i {
      width: 20px;
      height: 20px;
    }
  }
  .handle {
    i {
      width: 20px;
      height: 20px;
    }
  }
}
</style>
