<template>
  <div class="bottom-bar">
    <div class="left-btns">
      <i class="icon prev"></i>
      <i class="icon play"></i>
      <i class="icon next"></i>
      <span class="pass-time">{{passTime | formatTime}}</span>
    </div>
    <div class="time">
      <div class="progress-bar">
        <div class="pass-bar">
          <span class="point" draggable="true"><i class="icon"></i></span>
        </div>
      </div>
    </div>
    <div class="right-btns">
      <span class="duration">{{duration | formatTime}}</span>
      <div class="vol-setting">
        <i class="icon volumn"></i>
        <div class="progress-bar">
          <div class="pass-bar">
            <span class="point" draggable="true"><i class="icon"></i></span>
          </div>
        </div>
      </div>
      <div class="corner-btns">
        <i class="icon loop"></i>
        <i class="icon lyric"></i>
        <i class="icon list"></i>
      </div>
    </div>
  </div>
</template>
<script>
  export default {
    name: 'bottom-bar',
    data() {
      return {
        passTime: 82,
        duration: 290
      };
    },
    filters: {
      formatTime(duration) {
        if (duration <= 0) return '00:00';
        if (!duration) return '--:--';
        var min = ~~(duration / 60);
        min = (min + '').length === 1 ? '0' + min : min;
        var sec = Math.round(duration % 60);
        sec = (sec + '').length === 1 ? '0' + sec : sec;
        min = min || '00';
        sec = sec || '00';
        return min + ':' + sec;
      }
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
.bottom-bar {
  position: fixed;
  z-index: 2;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 60px;
  background-color: rgb(246, 246, 248);
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-top: 1px solid rgb(225, 225, 226);
  .left-btns {
    display: inline-flex;
    align-items: center;
    height: 100%;
    margin-left: 38px;
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
      margin: 0 28px;
    }
    .next {
      width: 36px;
      height: 36px;
    }
    .pass-time {
      margin-left: 38px;
    }
  }
  .time {
    position: absolute;
    left: 312px;
    right: 420px;
    .progress-bar {
      width: 100%;
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
  }
  .right-btns {
    display: inline-flex;
    justify-content: flex-start;
    align-items: center;
    margin-right: 16px;
    height: 100%;
    .duration {
      margin-right: 30px;
    }
    .vol-setting {
      display: inline-flex;
      justify-content: flex-start;
      align-items: center;
      .volumn {
        width: 20px;
        height: 20px;
        margin-right: 4px;
      }
      .progress-bar {
        position: relative;
        width: 125px;
        height: 6px;
        background-color: rgb(194, 194, 196);
        border-radius: 3px;
        .pass-bar {
          position: relative;
          top: 0;
          left: 0;
          width: 55px;
          height: 6px;
          background-color: rgb(232, 60, 60);
          border-radius: 3px;
          .point {
            display: none;
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
          &:hover {
            .point {
              display: inline-block;
            }
          }
        }
      }
    }
    .corner-btns {
      margin-left: 26px;
      i {
        width: 20px;
        height: 20px;
      }
      .loop {
        // background-image: url();
      }
      .lyric {
        margin: 0 20px;
        // background-image: url();
      }
      .list {
        width: 62px;
        // background-image: url();
      }
    }
  }
}
</style>
