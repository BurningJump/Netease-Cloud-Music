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
      <i class="icon email" @click="openMsgBox"></i>
      <i class="icon setting"></i>
    </div>
    <div class="handle">
      <i class="icon mini"></i>
      <i class="icon min"></i>
      <i class="icon max"></i>
      <i class="icon close"></i>
    </div>
    <div class="msgbox" v-show="showMsgBox">
      <div class="top-arrow"></div>
      <i class="icon close">×</i>
      <el-tabs v-model="activeTab" type="card" @tab-click="handleClick">
        <el-tab-pane label="私信" name="letter">
          <div class="no-letter" v-if="letterList.length===0">暂无私信内容</div>
          <li v-if="letterList.length!==0" class="letter-list" v-for="letter in letterList">
            <i class="icon reddot"></i>
            <img :src="letter.headThumb" alt="">
            <div class="detail">
              <div class="user-date">
                <span class="username">{{letter.from}}</span>
                <span class="date">{{letter.time}}</span>
              </div>
              <p class="msg">{{letter.msg}}</p>
            </div>
          </li>
        </el-tab-pane>
        <el-tab-pane label="评论" name="comment">
          <div class="no-comment" v-if="commentList.length===0">暂无评论内容</div>
          <li v-if="commentList.length!==0" class="comment-list" v-for="comment in commentList">
            <img :src="comment.headThumb" alt="">
            <div class="user-time">
              <span class="username">{{comment.from}}</span>
              <span class="time">{{comment.time}}</span>
            </div>
            <p>回复我：{{comment.msg}}</p>
            <div class="my-comment">我的评论：{{comment.myComment}}</div>
            <span class="reply"><i class="icon dialog"></i>回复</span>
          </li>
        </el-tab-pane>
        <el-tab-pane label="@我" name="viame">
          <div class="no-viame" v-if="viameList.length===0">暂无@我的内容</div>
          <li v-if="viameList.length!==0" class="viame-list"></li>
        </el-tab-pane>
        <el-tab-pane label="通知" name="notification">
          <div class="no-notification" v-if="notificationList.length===0">暂无通知内容</div>
          <li v-if="notificationList.length!==0" class="notification-list"></li>
        </el-tab-pane>
      </el-tabs>
    </div>
  </div>
</template>
<script>
  export default {
    name: 'top-bar',
    data() {
      return {
        username: 'burningjump',
        showMsgBox: true,
        activeTab: 'letter',
        letterList: [
          {
            hasRead: false,
            headThumb: 'www.baidu.com',
            from: '网易云音乐',
            time: '7月21日',
            msg: '节目：[李希侃&吕晨瑜：练习很辛苦，大厂男孩巴拉巴拉]'
          },
          {
            hasRead: false,
            headThumb: 'www.baidu.com',
            from: '云音乐小秘书',
            time: '7月10日',
            msg: '节目：[李希侃&吕晨瑜：练习很辛苦，大厂男孩巴拉巴拉]'
          },
          {
            hasRead: true,
            headThumb: 'www.baidu.com',
            from: '云音乐福利',
            time: '6月26日',
            msg: '节目：[李希侃&吕晨瑜：练习很辛苦，大厂男孩巴拉巴拉]'
          },
          {
            hasRead: true,
            headThumb: 'www.baidu.com',
            from: '潇洒小编',
            time: '4月23日',
            msg: '节目：[李希侃&吕晨瑜：练习很辛苦，大厂男孩巴拉巴拉]'
          }
        ],
        commentList: [
          {
            from: '怅号已注销',
            time: '4月27日',
            msg: '这个比它早',
            myComment: '跟windy hill旋律好像'
          },
          {
            from: '怅号已注销',
            time: '3月21日',
            msg: '这个比它早',
            myComment: '跟windy hill旋律好像'
          },
          {
            from: '怅号已注销',
            time: '2月3日',
            msg: '这个比它早',
            myComment: '跟windy hill旋律好像'
          }
        ],
        viameList: [],
        notificationList: []
      };
    },
    components: {},
    methods: {
      open(link) {
        this.$electron.shell.openExternal(link);
      },
      openMsgBox() {}
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
  .msgbox {
    position: absolute;
    z-index: 20;
    top: 60px;
    right: 0;
    width: 300px;
    height: 800px;
    background-color: #fff;
    box-shadow: -2px 2px 0 #ccc;
    .top-arrow {
      position: absolute;
      display: block;
      width: 0;
      height: 0;
      border-color: transparent;
      border-style: solid;
      top: -10px;
      left: 50%;
      margin-bottom: 3px;
      border-width: 11px;
      border-top-width: 0;
      border-bottom-color:#fff;
      &::after {
        position: absolute;
        display: block;
        width: 0;
        height: 0;
        border-color: transparent;
        border-style: solid;
        right: -11px;
        top: -12px;
        margin-left: -5px;
        border-top-width: 0;
        border-bottom-color:#fff;
        border-width: 11px;
      }
    }
    .close {
      width: 20px;
      height: 20px;
      background-color: #fff;
      font-size: 18px;
    }
    .letter-list {
      list-style: none;
      display: flex;
      justify-content: flex-start;
      align-items: center;
      margin: 10px 0;
      .reddot {
        width: 5px;
        height: 5px;
        background-color: red;
        border-radius: 50%;
      }
      img {
        width: 40px;
        height: 40px;
        background-color: #ccc;
        border-radius: 50%;
      }
      .detail {
        .user-date {
          display: inline-flex;
          justify-content: space-between;
          align-items: center;
          .username {}
          .date {}
        }
        .msg {
          overflow: hidden;
          text-overflow: ellipsis;
          white-space: nowrap;
        }
      }
    }
    .comment-list {
      list-style: none;
      display: flex;
      justify-content: flex-start;
      align-items: center;
      margin: 10px 0;
      img {
        width: 40px;
        height: 40px;
        background-color: #ccc;
        border-radius: 50%;
      }
      .my-comment {
        background-color: #ccc;
      }
    }
  }
}
</style>
