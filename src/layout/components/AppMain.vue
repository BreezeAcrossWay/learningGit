<template>
  <section class="app-main" :class="this.$route.path=='/dashboard'?'bgimg':this.$route.path=='/brand/list'?'bgimg2':''">
    <transition name="fade-transform" mode="out-in">
      <router-view :key="key" />
    </transition>
  </section>
</template>

<script>
export default {
  name: 'AppMain',
  computed: {
    key() {
      return this.$route.path
    }
  }
}
</script>

<style scoped>
.app-main {
  /*50 = navbar  */
  min-height: calc(100vh - 50px);
  width: 100%;
  position: relative;
  overflow: hidden;
}
.bgimg {
  background-image: url('../../assets/imgs/bg5.jpg');
  background-size:cover;
}
.bgimg2 {
  background-image: url('../../assets/imgs/bg7.jpg');
  background-size:cover;
}
.fixed-header+.app-main {
  padding-top: 50px;
}
</style>

<style lang="scss">
// fix css style bug in open el-dialog
.el-popup-parent--hidden {
  .fixed-header {
    padding-right: 15px;
  }
}
</style>
