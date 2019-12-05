<template>
  <div id="app">
  <el-menu
    :default-active="activeIndex2"
    class="header"
    mode="horizontal"
    @select="handleSelect"
    background-color="#545c64"
    text-color="#fff"
    active-text-color="#ffd04b">
    <h1 id="title">Simple Blog</h1>
    <el-menu-item index="1">登陆</el-menu-item>
    <el-menu-item index="2">注册</el-menu-item>
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
.el-menu--horizontal>.el-menu-item {
    float: right;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
