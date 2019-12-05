<template>
  <div class="">
      <ul>
        <li v-for="item in courseList" :key="item">
          <el-container >
            <el-main>
              <router-link :to="{'path':'/article/details/'+item.id}">{{item.name}}</router-link>
            </el-main>
          </el-container>
        </li>
      </ul>
      <el-pagination
        layout="prev, pager, next"
        :total="50">
      </el-pagination>
  </div>
</template>

<script>
export default {
  name: 'index',
  data () {
    return {
      msg: '',
      courseList: []
    }
  },
  mounted: function() {
      //当组件一加载的时候就应该去数据库去获取数据
      this.initCourses()
  },
  methods:{
    initCourses: function () {
      var that = this
      that.courseList.push({
          id: 1,
          name: "blog1"
          })  
      that.courseList.push({
          id: 2,
          name: "blog2"
          })   
    //   var that = this
    //   this.$axios.request({
    //       url:'https://localhost/article/{id}',
    //       method:"GET"
    //   }).then(function (response) {
    //     console.log(response);
    //     that.courseList = response.data.courseList
    //   })
    }
  }

}

</script>
<style>
.el-pagination {
  position:fixed;
  left: 20px;
  right: 20px;
  bottom:0px;
  margin-bottom: 20px;
}
.el-container {
  height: 100px;
  width: 700px;
  box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);
  margin: 5px auto;
}
ul {
  margin: 0;
  padding: 0;
}
li {
  list-style-type :none;
}
a {
  float: left;
  text-decoration: none;
}
.router-link-active {
  
  text-decoration: none;
}
</style>