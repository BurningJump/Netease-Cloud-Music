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
                <span class="editor-recommend">根据您的音乐口味生成每日更新</span>
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
                <span class="editor-recommend">{{list.editorRecommend}}</span>
                <span class="play-btn">
                  <i class="icon play"></i>
                </span>
              </div>
              <p class="title">{{list.title}}</p>
            </li>
          </ul>
        </section>
        <section class="exclusive">
          <div class="subtitle">
            <span>独家放送</span>
            <a href="">更多<i class="el-icon-arrow-right"></i></a>
          </div>
          <ul>
            <li class="card" v-for="list in exclusiveLists">
              <div class="cover">
                <img :src="list.thumb" alt="">
                <i v-show="list.type==='article'" class="icon book"></i>
                <i v-show="list.type==='video'" class="icon video"></i>
              </div>
              <p class="title">{{list.title}}</p>
            </li>
          </ul>
        </section>
        <section class="latest">
          <div class="subtitle">
            <span>最新音乐</span>
            <a href="">更多<i class="el-icon-arrow-right"></i></a>
          </div>
          <div class="latest-list">
            <div class="music-list" v-for="(music, index) in latestMusics">
              <span class="num">{{index+1}}</span>
              <div class="cover">
                <img :src="music.thumb" alt="">
                <span class="play-btn">
                  <i class="icon play"></i>
                </span>
              </div>
              <div class="title-name">
                <span class="title">{{music.title}}</span>
                <p class="name">
                  <i v-show="music.sq" class="icon sq"></i>
                  <i v-show="music.mv" class="icon mv"></i>
                  <span>{{music.singer}}</span>
                </p>
              </div>
            </div>
          </div>
        </section>
        <section class="mv">
          <div class="subtitle">
            <span>推荐MV</span>
            <a href="">更多<i class="el-icon-arrow-right"></i></a>
          </div>
          <ul>
            <li class="card" v-for="mv in MVs">
              <div class="cover">
                <img :src="mv.thumb" alt="">
                <div class="play-times">
                  <i class="icon video"></i>
                  <span>{{mv.times}}</span>
                </div>
                <span class="editor-recommend">{{mv.editorRecommend}}</span>
              </div>
              <p class="title">{{mv.title}}</p>
            </li>
          </ul>
        </section>
        <section class="anchor">
          <div class="subtitle">
            <span>主播电台</span>
            <a href="">更多<i class="el-icon-arrow-right"></i></a>
          </div>
          <ul>
            <li class="card" v-for="anchor in anchors">
              <div class="cover">
                <img :src="anchor.thumb" alt="">
                <span v-show="anchor.type" class="vip">付费精品</span>
                <span>{{anchor.name}}</span>
              </div>
              <p class="title">{{anchor.title}}</p>
            </li>
          </ul>
        </section>
        <div class="adjust-list">
          <p class="note">现在可以根据个人爱好，自由调整首页栏目顺序啦~</p>
          <span class="btn">调整栏目顺序</span>
        </div>
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
            editorRecommend: '编辑推荐：乌云乌云快走开',
            title: '城市季候|跟我逃离或是大梦一场'
          },
          {
            times: '31万',
            thumb: 'www.baidu.com',
            editorRecommend: '编辑推荐：爱到满溢，Rapper们唱出口的情话',
            title: '『古风田园』云烟皆过，归往竹林深处'
          },
          {
            times: '102万',
            thumb: 'www.baidu.com',
            editorRecommend: '根据你的风格推荐',
            title: '城市季候|跟我逃离或是大梦一场'
          },
          {
            times: '102万',
            thumb: 'www.baidu.com',
            editorRecommend: '根据你喜欢的单曲《***》推荐',
            title: '城市季候|跟我逃离或是大梦一场'
          },
          {
            times: '102万',
            thumb: 'www.baidu.com',
            editorRecommend: '根据你喜欢的单曲《***》推荐',
            title: '城市季候|跟我逃离或是大梦一场'
          },
          {
            times: '102万',
            thumb: 'www.baidu.com',
            editorRecommend: '根据你喜欢的单曲《***》推荐',
            title: '城市季候|跟我逃离或是大梦一场'
          },
          {
            times: '102万',
            thumb: 'www.baidu.com',
            editorRecommend: '根据你喜欢的单曲《***》推荐',
            title: '城市季候|跟我逃离或是大梦一场'
          },
          {
            times: '102万',
            thumb: 'www.baidu.com',
            editorRecommend: '根据你喜欢的单曲《***》推荐',
            title: '城市季候|跟我逃离或是大梦一场'
          },
          {
            times: '102万',
            thumb: 'www.baidu.com',
            editorRecommend: '根据你喜欢的单曲《***》推荐',
            title: '城市季候|跟我逃离或是大梦一场'
          }
        ],
        exclusiveLists: [
          {
            type: 'article',
            thumb: 'www.baidu.com',
            title: '【一周音乐视频榜】第32期：拯救夏日歌荒，不如来点酷炫说唱'
          },
          {
            type: 'video',
            thumb: 'www.baidu.com',
            title: '跨越时空的动人故事：《时间飞行》甜美女声版'
          },
          {
            type: 'video',
            thumb: 'www.baidu.com',
            title: '夏日清新单曲《蜜蜂》，抒情歌声记录点滴心绪'
          }
        ],
        latestMusics: [
          {
            title: '夜曲',
            singer: '周杰伦',
            thumb: 'www.baidu.com',
            sq: true,
            mv: true
          },
          {
            title: '枫叶',
            singer: '周杰伦',
            thumb: 'www.baidu.com',
            sq: true,
            mv: true
          },
          {
            title: '吻别',
            singer: '张学友',
            thumb: 'www.baidu.com',
            sq: false,
            mv: false
          },
          {
            title: '少女的祈祷',
            singer: '杨千嬅',
            thumb: 'www.baidu.com',
            sq: true,
            mv: true
          },
          {
            title: '新不了情',
            singer: '萧敬腾',
            thumb: 'www.baidu.com',
            sq: true,
            mv: true
          },
          {
            title: '我还想她',
            singer: '林俊杰',
            thumb: 'www.baidu.com',
            sq: true,
            mv: true
          },
          {
            title: '一生中最爱',
            singer: '谭咏麟',
            thumb: 'www.baidu.com',
            sq: true,
            mv: true
          },
          {
            title: '重复犯错',
            singer: '古巨基',
            thumb: 'www.baidu.com',
            sq: true,
            mv: true
          },
          {
            title: '演员',
            singer: '薛之谦',
            thumb: 'www.baidu.com',
            sq: true,
            mv: true
          },
          {
            title: '煎熬',
            singer: '李佳薇',
            thumb: 'www.baidu.com',
            sq: true,
            mv: true
          }
        ],
        MVs: [
          {
            thumb: 'www.baidu.com',
            times: '38万',
            title: 'Bruce Lee李小龙',
            name: 'AI Rocco / 王嘉尔'
          },
          {
            thumb: 'www.baidu.com',
            times: '21777',
            title: 'If Love Is The Law',
            name: 'Noel Gallagher\'s High Flying Birds'
          },
          {
            thumb: 'www.baidu.com',
            times: '2756',
            title: '1999 | 18/07/17 Live',
            name: 'Peterpan Complex / 郑仁'
          }
        ],
        anchors: [
          {
            type: 'vip',
            thumb: 'www.baidu.com',
            name: '陈立客厅',
            title: '影响你未来的100次心理谈话'
          },
          {
            type: 'normal',
            thumb: 'www.baidu.com',
            name: '王东电台',
            title: 'DJ王东的私人音乐频道'
          },
          {
            type: 'vip',
            thumb: 'www.baidu.com',
            name: '七天改善睡眠冥想',
            title: '睡前10分钟 全天幸福感'
          },
          {
            type: 'normal',
            thumb: 'www.baidu.com',
            name: '女生宿舍 | 来聊天呐',
            title: '啥都能聊得创意脱口秀'
          },
          {
            type: 'normal',
            thumb: 'www.baidu.com',
            name: '航空大话',
            title: '聊航空，说大话'
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
  margin-bottom: 61px;
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
  .recommend {
    ul {
      margin: 10px auto 0;
      list-style: none;
      display: flex;
      justify-content: flex-start;
      align-items: center;
      flex-wrap: wrap;
      width: 930px;
      li {
        width: 170px;
        margin-right: 20px;
        margin-bottom: 30px;
        p {
          height: 30px;
          text-align: left;
          margin-top: 10px;
        }
      }
      li:nth-child(5n) {
        margin-right: 0;
      }
      .card {
        .cover {
          width: 100%;
          height: 170px;
          border: 1px solid rgb(225, 225, 226);
          background-color: #ccc;
        }
        .time {
          display: flex;
          justify-content: center;
          align-items: center;
          flex-direction: column;
          background-color: #fff;
          .day {
            color: rgb(149, 102, 102);
          }
          .date {
            display: block;
            font-size: 100px;
            color: rgb(198, 47, 47);
          }
        }
      }
    }
  }
  .exclusive {
    ul {
      margin: 10px auto 0;
      list-style: none;
      display: flex;
      justify-content: flex-start;
      align-items: center;
      flex-wrap: wrap;
      width: 930px;
      li {
        width: 296px;
        margin-right: 20px;
        margin-bottom: 30px;
        .cover {
          width: 100%;
          height: 170px;
          border: 1px solid rgb(225, 225, 226);
          background-color: #ccc;
        }
        p.title {
          height: 30px;
          text-align: left;
          margin-top: 10px;
        }
      }
      li:last-child {
        margin-right: 0;
      }
    }
  }
  .latest {
    width: 930px;
    .latest-list {
      display: flex;
      flex-direction: column;
      flex-wrap: wrap;
      width: 100%;
      height: 302px;
      border: 1px solid #ccc;
      box-sizing: border-box;
      .music-list:nth-child(2),
      .music-list:nth-child(4),
      .music-list:nth-child(7),
      .music-list:nth-child(9), {
        background-color: #ebeef5;
      }
      .music-list {
        display: inline-flex;
        justify-content: flex-start;
        align-items: center;
        width: 50%;
        height: 60px;
        border-right: 1px solid #ccc;
        &:hover {
          background-color: #ccc;
        }
        .num {
          margin: 0 15px 0 10px;
        }
        .cover {
          position: relative;
          margin-right: 10px;
          cursor: pointer;
          img {
            width: 40px;
            height: 40px;
            background-color: #ccc;
          }
          .play-btn {
            position: absolute;
            top: 10px;
            left: 10px;
            width: 20px;
            height: 20px;
            border: 1px solid #fff;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            .play {
              width: 10px;
              height: 10px;
            }
          }
        }
        .title-name {
          .title {}
          .name {
            .sq {
              width: 20px;
              height: 10px;
              margin-right: 10px;
            }
            .mv {
              width: 20px;
              height: 10px;
              margin-right: 10px;
            }
            span {
              cursor: pointer;
            }
          }
        }
      }
    }
  }
  .mv {
    ul {
      margin: 10px auto 0;
      list-style: none;
      display: flex;
      justify-content: flex-start;
      align-items: center;
      flex-wrap: wrap;
      width: 930px;
      li {
        width: 296px;
        margin-right: 20px;
        margin-bottom: 30px;
        .cover {
          width: 100%;
          height: 170px;
          border: 1px solid rgb(225, 225, 226);
          background-color: #ccc;
        }
        p.title {
          height: 30px;
          text-align: left;
          margin-top: 10px;
        }
      }
      li:last-child {
        margin-right: 0;
      }
    }
  }
  .anchor {
    border-bottom: 1px solid rgb(225, 225, 226);
    ul {
      margin: 10px auto 0;
      list-style: none;
      display: flex;
      justify-content: flex-start;
      align-items: center;
      flex-wrap: wrap;
      width: 930px;
      li {
        width: 170px;
        margin-right: 20px;
        margin-bottom: 30px;
        .cover {
          width: 100%;
          height: 170px;
          border: 1px solid rgb(225, 225, 226);
          background-color: #ccc;
        }
        p.title {
          height: 30px;
          text-align: left;
          margin-top: 10px;
        }
      }
      li:last-child {
        margin-right: 0;
      }
    }
  }
  .adjust-list {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    .note {}
    .btn {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 120px;
      height: 30px;
      border: 1px solid #ccc;
      border-radius: 6px;
      cursor: pointer;
      &:hover {
        border: 1px solid #000;
      }
    }
  }

}
</style>
