<template>
  <div class="main-block">
    
  </div>
</template>
<script>
  export default {
    name: 'main-block',
    components: {},
    methods: {
      open(link) {
        this.$electron.shell.openExternal(link);
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
}
</style>
