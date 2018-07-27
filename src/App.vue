<template>
  <div id="app">
    <Header></Header>
    <router-view name="main"></router-view>
    <router-view name="article"></router-view>
  </div>
</template>

<script>
import Header from './components/header'
import PostList from './components/PostList'
export default {
  name: 'App',
  components:{Header,PostList}
}
</script>

<style>
#app {

}
</style>
