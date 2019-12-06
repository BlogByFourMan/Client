<template>
  <div class="">
      <ul>
        <li v-for="item in articlesList" :key="item">
          <el-container >
            <el-main>
              <div class="title">
                <router-link :to="{'path':'/article/details/'+item.id}">{{item.title}}</router-link>
              </div>          
              <div class="extra">
                <div class="author">{{item.author}}</div>
                <div class="date">{{item.date}}</div>
              </div>
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
      articlesList: []
    }
  },
  mounted: function() {
      //当组件一加载的时候就应该去数据库去获取数据
      this.initArticles()
  },
  methods:{
    initArticles: function () {
      var that = this
      that.articlesList.push({
          id: 1,
          title: "通过各种简单案例，让你彻底搞懂 MySQL 中的锁机制与 MVCC",
          date: "2019-12-05",
          author: "董旭阳TonyDong"
          })  
      that.articlesList.push({
          id: 2,
          title: "shell脚本：备份数据库、代码上线",
          date: "2014-01-12",
          author: "Asnfy"
          })   
      this.$axios.request({
          url:'https://localhost/articles?page=1',
          method:"GET",
          responseType:'json'
      }).then(function (response) {
        console.log(response);
        that.articlesList = response.data
      })
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
  width: 800px;
  box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);
  margin: 5px auto;
}
ul {
  margin: 0;
  padding: 0;
}
li {
  list-style-type :none;
  position: relative;
}
a {
  float: left;
  text-decoration: none;
}
.router-link-active {
  
  text-decoration: none;
}
.title {
  height: 30px;
}
.extra {
  margin-top: 12px;
  bottom: 10px;
  font-size: 12px;
}
.author {
  float: left;
}
.date {
  float: right;
}
</style>