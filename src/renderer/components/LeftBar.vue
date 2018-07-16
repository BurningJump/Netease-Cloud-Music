<template>
  <div class="left-bar">
    <ul class="recommend">
      <li>推荐</li>
      <li>
        <i class="icon music"></i>
        <span>发现音乐</span>
      </li>
      <li>
        <i class="icon radar"></i>
        <span>私人FM</span>
      </li>
      <li>
        <i class="icon video"></i>
        <span>视频</span>
      </li>
      <li>
        <i class="icon friend"></i>
        <span>朋友</span>
      </li>
    </ul>
    <ul class="my-music">
      <li>我的音乐</li>
      <li>
        <i class="icon disc"></i>
        本地音乐
      </li>
      <li>
        <i class="icon download"></i>
        下载管理
      </li>
      <li>
        <i class="icon cloud"></i>
        我的音乐云盘
      </li>
      <li>
        <i class="icon radio"></i>
        我的电台
      </li>
      <li>
        <i class="icon collection"></i>
        我的收藏
      </li>
    </ul>
    <ul class="created-playlist">
      <li>创建的歌单</li>
      <li>
        <i class="icon heart"></i>
        <span>我喜欢的音乐</span>
      </li>
      <li v-for="playlist in playlists">
        <i class="icon playlist"></i>
        <span>{{playlist.name}}</span>
      </li>
    </ul>
  </div>
</template>
<script>
  export default {
    name: 'left-bar',
    data() {
      return {
        playlists: [
          {
            name: '程序员'
          },
          {
            name: '英文'
          },
          {
            name: '女毒'
          },
          {
            name: '纯音乐'
          }
        ]
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
.left-bar {
  position: absolute;
  top: 60px;
  bottom: 60px;
  left: 0;
  width: 250px;
  background-color: rgb(245, 245, 247);
  ul {
    width: 100%;
    li:first-child {
      padding-left: 12px;
      cursor: default;
    }
    li {
      display: flex;
      justify-content: flex-start;
      align-items: center;
      width: 100%;
      height: 40px;
      color: rgb(92, 92, 92);
      background-color: rgb(245, 245, 247);
      cursor: pointer;
      i {
        width: 20px;
        height: 20px;
        margin-left: 22px;
        margin-right: 13px;
      }
    }
    .is-active {
      color: #000;
      background-color: rgb(230, 231, 234 );
      border-left: 3px solid rgb(198, 47, 47);
    }
  }
}
</style>
