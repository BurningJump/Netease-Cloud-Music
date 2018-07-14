<template>
  <div class="bottom-bar">
    
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
  background-color: #C20C0C;
}
</style>
