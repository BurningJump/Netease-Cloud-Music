<template>
  <div class="left-bar">
    <div class="collapse-list">
      <span>推荐</span>
    </div>
    <ul class="recommend">
      <li :class="activeList === 'find' ? 'active-list' : ''">
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
    <div class="collapse-list">
      <span>我的音乐</span>
    </div>
    <ul class="my-music">
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
    <div class="collapse-list" @click="showCreatedList=!showCreatedList">
      <span>创建的歌单</span>
      <span class="add">+</span>
      <i class="el-icon-arrow-down" v-show="showCreatedList"></i>
      <i class="el-icon-arrow-right" v-show="!showCreatedList"></i>
    </div>
    <el-collapse-transition>
      <ul class="created-playlist" v-show="showCreatedList">
        <li>
          <i class="icon heart"></i>
          <span>我喜欢的音乐</span>
          <i class="icon volume"></i>
        </li>
        <li v-for="playlist in playlists">
          <i class="icon playlist"></i>
          <span>{{playlist.name}}</span>
          <i class="icon volume"></i>
        </li>
      </ul>
    </el-collapse-transition>
    <div class="collapse-list" @click="showCollectionList=!showCollectionList">
      <span>收藏的歌单</span>
      <i class="el-icon-arrow-down" v-show="showCollectionList"></i>
      <i class="el-icon-arrow-right" v-show="!showCollectionList"></i>
    </div>
    <el-collapse-transition>
      <ul class="collection-list" v-show="showCollectionList">
        <li v-for="collectionList in collectionLists">
          <i class="icon playlist"></i>
          <span>{{collectionList.name}}</span>
          <i class="icon volume"></i>
        </li>
      </ul>
    </el-collapse-transition>
    <div class="current-song">
      <div class="cover-thumb">
        <img src="" alt="">
        <span class="expand-mask"></span>
      </div>
      <div class="title-singer">
        <div class="title">
          <span>{{currentSong.title}}</span>
        </div>
        <div class="singer">
          <span>{{currentSong.singer}}</span>
        </div>
      </div>
      <div class="collect-share">
        <i class="icon love"></i>
        <i class="icon share"></i>
      </div>
    </div>
  </div>
</template>
<script>
  export default {
    name: 'left-bar',
    data() {
      return {
        activeList: 'find',
        currentSong: {
          singer: '张学友',
          title: '爱上张无忌（2003年版《倚天屠龙记》片尾曲）'
        },
        showCreatedList: true,
        showCollectionList: true,
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
        ],
        collectionLists: [
          {
            name: '为听他的配乐才去看电影'
          },
          {
            name: '【骨灰级】程序员编程必备音乐'
          },
          {
            name: '头文字D中那些爆燃的BGM'
          },
          {
            name: '源自纪录片的伤感曲调'
          },
          {
            name: '爱尔兰哨笛'
          },
          {
            name: '万次评论只为这个旋律'
          },
          {
            name: '华语优质女声|感动不用歇斯底里'
          },
          {
            name: '两百位日本配乐作曲家，每人一首良曲'
          },
          {
            name: '冷门华语集，你未发现的好歌。'
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
  overflow: scroll;
  border-right: 1px solid rgb(225, 225, 226);
  &::-webkit-scrollbar {
    width: 10px;
    height: 10px;
    background-color: transparent;
  }
  &::-webkit-scrollbar-track {
    display: none;
  }
  &::-webkit-scrollbar-thumb {
    border-radius: 20px;
    width: 10px;
    height: 370px;
    background: rgb(225, 225, 226);
    &:hover {
      background: rgb(207, 207, 209);
    }
  }
  &::-webkit-scrollbar-button:start {
    display: none;
  }
  &::-webkit-scrollbar-button:end {
    display: none;
  }
  &::-webkit-scrollbar-corner {
    display: none;
  }
  .collapse-list {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 229px;
    height: 50px;
    span {
      margin-left: 12px;
    }
    .add {
      margin: 0;
      width: 20px;
      height: 20px;
      color: #fff;
      font-size: 18px;
      font-weight: bold;
      display: inline-flex;
      justify-content: center;
      align-items: center;
      background-color: #ccc;
      border-radius: 50%;
      &:hover {
        background-color: #000;
      }
    }
    i {
      margin-right: 12px;
      cursor: pointer;
    }
  }
  ul {
    width: 229px;
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
      span {
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
        font-size: 14px;
      }
    }
    .active-list {
      color: #000;
      background-color: rgb(230, 231, 234 );
      border-left: 3px solid rgb(198, 47, 47);
    }
  }
  .collection-list {
    margin-bottom: 70px;
  }
  .current-song {
    position: fixed;
    left: 0;
    bottom: 60px;
    width: 250px;
    height: 70px;
    background-color: rgb(245, 245, 247);
    display: flex;
    justify-content: space-around;
    align-items: center;
    border-top: 1px solid rgb(225, 225, 226);
    .cover-thumb {
      position: relative;
      img {
        width: 53px;
        height: 53px;
        background-color: #c731db;
      }
      .expand-mask {
        position: absolute;
        top: 0;
        left: 0;
        display: none;
        width: 53px;
        height: 53px;
      }
    }
    .title-singer {
      display: flex;
      flex-direction: column;
      width: 140px;
      .title, .singer {
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
      }
    }
    .collect-share {
      display: flex;
      flex-direction: column;
      i {
        width: 18px;
        height: 18px;
      }
    }
    &:hover {
      .expand-mask {
        display: block;
      }
    }
  }
}
</style>
