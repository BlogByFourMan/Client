<template>
  <div id="app">
  <el-menu
    :router="true"
    :default-active="this.$route.path"
    class="header"
    mode="horizontal"
    @select="handleSelect"
    background-color="#545c64"
    text-color="#fff"
    >
    <h1 id="title">Simple Blog</h1>
    <router-link to='/' style='float:left'>
      <el-menu-item index="3" >主页</el-menu-item>
    </router-link>
    <router-link to='/join' style='float:right'>
      <el-menu-item index="2" route="/join">注册</el-menu-item>
    </router-link>
    <router-link to='/login' style='float:right'>
      <el-menu-item index="1">登陆</el-menu-item>
    </router-link>
  </el-menu>
    <!--<img src="./assets/logo.png">-->
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
body {
  margin: 0;
}
#title {
  float: left;
  font-size: 30px;
  margin-block-start: 10px;
  margin-block-end: 10px;
  margin-inline-start: 0px;
  margin-inline-end: 0px;
  color: #FFF;
  width: 200px;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
