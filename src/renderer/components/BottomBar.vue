<template>
  <div class="bottom-bar">
    <div class="btns">
      <i class="icon prev"></i>
      <i class="icon play"></i>
      <i class="icon next"></i>
    </div>
    <div class="time">
      <span class="pass-time"></span>
      <div class="progress-bar">
        <div class="pass-bar">
          <span class="point"><i class="icon"></i></span>
        </div>
      </div>
      <span class="duration"></span>
    </div>
  </div>
</template>
<script>
  export default {
    name: 'bottom-bar',
    components: {},
    methods: {
      open(link) {
        this.$electron.shell.openExternal(link);
      }
    }
  };
</script>
<style lang="scss">
.bottom-bar {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 60px;
  background-color: rgb(246, 246, 248);
  display: flex;
  align-items: center;
  .btns {
    i {
      border-radius: 50%;
    }
    .prev {
      width: 36px;
      height: 36px;
    }
    .play {
      width: 44px;
      height: 44px;
    }
    .next {
      width: 36px;
      height: 36px;
    }
  }
  .time {
    .pass-time {}
    .progress-bar {
      position: relative;
      width: 546px;
      height: 6px;
      background-color: rgb(194, 194, 196);
      border-radius: 3px;
      .pass-bar {
        position: relative;
        top: 0;
        left: 0;
        width: 250px;
        height: 6px;
        background-color: rgb(232, 60, 60);
        border-radius: 3px;
        .point {
          position: absolute;
          right: 0;
          top: -5px;
          width: 18px;
          height: 16px;
          border-radius: 9px;
          background-color: #fff;
          cursor: pointer;
          border: 1px solid rgb(203, 203, 203);
          i {
            background-color: rgb(232, 60, 60);
          }
        }
      }
    }
    .duration {}
  }
}
</style>
