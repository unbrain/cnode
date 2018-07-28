<template>
  <div id="app">
    <Header></Header>
    <div class="main">
      <router-view name="sliderbar"></router-view>
      <router-view name="main"></router-view>
    </div>

  </div>
</template>

<script>
import Header from './components/header'
import PostList from './components/PostList'
export default {
  name: 'App',
  components: { Header, PostList }
}
</script>

<style lang="scss">
#app {
  background-color: #e1e1e1;
  .main {
    width: 80%;
    margin: 0 auto;
  }
}
</style>
