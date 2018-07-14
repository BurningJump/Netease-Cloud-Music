<template>
  <div class="left-bar">
    
  </div>
</template>
<script>
  export default {
    name: 'left-bar',
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
}
</style>
