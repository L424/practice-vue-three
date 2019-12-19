<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
<!--    <router-view v-if="isRouterAlive"></router-view>-->
  </div>
</template>
<!--<script>-->
<!--  export default {-->
<!--    name:app,-->
<!--    data () {-->
<!--      return {-->
<!--        isRouterAlive: true-->
<!--      }-->
<!--    }-->
<!--  }-->
<!--</script>-->
<style lang="scss">

</style>
