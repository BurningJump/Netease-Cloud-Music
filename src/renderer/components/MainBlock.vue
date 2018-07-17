<template>
  <div class="main-block">
    <el-tabs v-model="activeName" @tab-click="handleClick">
      <el-tab-pane label="个性推荐" name="recommend">
        <el-carousel type="card" indicator-position="outside" arrow="hover">
          <el-carousel-item v-for="item in 8" :key="item">
            <h3>{{ item }}</h3>
          </el-carousel-item>
        </el-carousel>
      </el-tab-pane>
      <el-tab-pane label="歌单" name="list">歌单</el-tab-pane>
      <el-tab-pane label="主播电台" name="radio">
        <el-carousel type="card" indicator-position="outside" arrow="hover">
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
        activeName: 'recommend'
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
  bottom: 60px;
  right: 0;
  left: 250px;
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
}
</style>
