<template>
  <div class="main-block">
    <el-tabs v-model="activeName" @tab-click="handleClick">
      <el-tab-pane label="个性推荐" name="recommend">
        <el-carousel type="card" indicator-position="outside" arrow="hover" height="250px" :autoplay="false">
          <el-carousel-item v-for="item in 8" :key="item">
            <h3>{{ item }}</h3>
          </el-carousel-item>
        </el-carousel>
        <section class="recommend">
          <div class="subtitle">
            <span>推荐歌单</span>
            <a href="">更多<i class="el-icon-arrow-right"></i></a>
          </div>
          <ul>
            <li class="card">
              <div class="time cover">
                <span class="day">{{day}}</span>
                <span class="date">{{date}}</span>
              </div>
              <p class="title">每日歌曲推荐</p>
            </li>
            <li class="card" v-for="list in recommendLists">
              <div class="cover">
                <img :src="list.thumb" alt="">
                <div class="play-times">
                  <i class="icon listen"></i>
                  <span>{{list.times}}</span>
                </div>
                <span class="play-btn">
                  <i class="icon play"></i>
                </span>
              </div>
              <p class="title">{{list.title}}</p>
            </li>
          </ul>
        </section>
      </el-tab-pane>
      <el-tab-pane label="歌单" name="list">歌单</el-tab-pane>
      <el-tab-pane label="主播电台" name="radio">
        <el-carousel type="card" indicator-position="outside" arrow="hover" height="250px" :autoplay="false">
          <el-carousel-item v-for="item in 5" :key="item">
            <h3>{{ item }}</h3>
          </el-carousel-item>
        </el-carousel>
      </el-tab-pane>
      <el-tab-pane label="排行榜" name="rank">排行榜</el-tab-pane>
      <el-tab-pane label="歌手" name="singer">歌手</el-tab-pane>
      <el-tab-pane label="最新音乐" name="latest">最新音乐</el-tab-pane>
    </el-tabs>
  </div>
</template>
<script>
  export default {
    name: 'main-block',
    data() {
      return {
        activeName: 'recommend',
        recommendLists: [
          {
            times: '102万',
            thumb: 'www.baidu.com',
            title: '城市季候|跟我逃离或是大梦一场'
          },
          {
            times: '31万',
            thumb: 'www.baidu.com',
            title: '『古风田园』云烟皆过，归往竹林深处'
          },
          {
            times: '102万',
            thumb: 'www.baidu.com',
            title: '城市季候|跟我逃离或是大梦一场'
          },
          {
            times: '102万',
            thumb: 'www.baidu.com',
            title: '城市季候|跟我逃离或是大梦一场'
          },
          {
            times: '102万',
            thumb: 'www.baidu.com',
            title: '城市季候|跟我逃离或是大梦一场'
          },
          {
            times: '102万',
            thumb: 'www.baidu.com',
            title: '城市季候|跟我逃离或是大梦一场'
          },
          {
            times: '102万',
            thumb: 'www.baidu.com',
            title: '城市季候|跟我逃离或是大梦一场'
          },
          {
            times: '102万',
            thumb: 'www.baidu.com',
            title: '城市季候|跟我逃离或是大梦一场'
          },
          {
            times: '102万',
            thumb: 'www.baidu.com',
            title: '城市季候|跟我逃离或是大梦一场'
          }
        ],
        day: '星期六',
        date: '21'
      };
    },
    components: {},
    methods: {
      open(link) {
        this.$electron.shell.openExternal(link);
      },
      handleClick(tab, event) {
        console.log(tab, event);
      }
    }
  };
</script>
<style lang="scss">
.main-block {
  position: absolute;
  top: 60px;
  bottom: 61px;
  right: 0;
  left: 251px;
  width: 100%;
  background-color: rgb(250, 250, 250);
  .el-carousel__item h3 {
    color: #475669;
    font-size: 18px;
    opacity: 0.75;
    line-height: 300px;
    margin: 0;
  }
  
  .el-carousel__item:nth-child(2n) {
    background-color: #99a9bf;
  }
  
  .el-carousel__item:nth-child(2n+1) {
    background-color: #d3dce6;
  }

  section {
    ul {
      list-style: none;
      display: flex;
      justify-content: flex-start;
      align-items: center;
      flex-wrap: wrap;
      li {}
      .card {
        .cover {
          width: 170px;
          height: 170px;
          border: 1px solid rgb(225, 225, 226);
          background-color: #ccc;
        }
        .time {
          background-color: #fff;
          .day {}
          .date {
            font-size: 40px;
          }
        }
      }
    }
  }
  .recommend {}
    .subtitle {
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 1px solid rgb(225, 225, 226);
      span {
        font-size: 20px;
      }
      a {
        font-size: 14px;
        color: rgb(102, 102, 102);
        text-decoration: none;
      }
    }

}
</style>
