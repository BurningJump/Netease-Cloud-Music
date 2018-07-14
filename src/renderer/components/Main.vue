<template>
  <div class="main">
    
  </div>
</template>
<script>
  export default {
    name: 'main',
    components: {},
    methods: {
      open(link) {
        this.$electron.shell.openExternal(link);
      }
    }
  };
</script>
<style lang="scss">
.main {
  position: absolute;
  top: 60px;
  bottom: 60px;
  right: 0;
  width: 100%;
  background-color: rgb(250, 250, 250);
}
</style>
