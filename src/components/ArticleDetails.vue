<template>
  <div class="main">
    <div class = "title">
      <h2>{{ article.title }}</h2>
    </div>
    <div class = "extra">
      <div class="date">{{article.date}}</div>
      <div class="author">{{article.author}}</div>
    </div>
    <div class = "content">
      {{ article.content }}
      <br>
      <br>
      <br>
    </div>
    <div class = "comments">
      <div class="addComment">
        <el-input v-model="toAdd" placeholder="添加评论..." class='inputClass'></el-input>
        <el-button type="primary" size="mini">评论</el-button>
      </div>
      <ul>
        <li v-for="item in comments" :key="item">      
          <div class="header">
            <div class="author">{{item.user}}</div>
            <div class="date">{{item.date}}</div>
          </div>
          <div class = "comment">{{item.content}}</div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'article details',
  data () {
    return {
      article: {
        id: this.$route.params.id,
        title: "通过各种简单案例，让你彻底搞懂 MySQL 中的锁机制与 MVCC",
        author: "董旭阳TonyDong",
        date: "2019-12-05",
        content: "锁（Locking）是数据库在并发访问时保证数据一致性和完整性的主要机制。在 MySQL 中，不同存储引擎使用不同的加锁方式；我们以 InnoDB 存储引擎为例介绍 MySQL 中的锁机制，其他存储引擎中的锁相对简单一些。锁（Locking）是数据库在并发访问时保证数据一致性和完整性的主要机制。在 MySQL 中，不同存储引擎使用不同的加锁方式；我们以 InnoDB 存储引擎为例介绍 MySQL 中的锁机制，其他存储引擎中的锁相对简单一些。\n锁（Locking）是数据库在并发访问时保证数据一致性和完整性的主要机制。在 MySQL 中，不同存储引擎使用不同的加锁方式；我们以 InnoDB 存储引擎为例介绍 MySQL 中的锁机制，其他存储引擎中的锁相对简单一些。\n锁（Locking）是数据库在并发访问时保证数据一致性和完整性的主要机制。在 MySQL 中，不同存储引擎使用不同的加锁方式；我们以 InnoDB 存储引擎为例介绍 MySQL 中的锁机制，其他存储引擎中的锁相对简单一些。\n锁（Locking）是数据库在并发访问时保证数据一致性和完整性的主要机制。在 MySQL 中，不同存储引擎使用不同的加锁方式；我们以 InnoDB 存储引擎为例介绍 MySQL 中的锁机制，其他存储引擎中的锁相对简单一些。\n锁（Locking）是数据库在并发访问时保证数据一致性和完整性的主要机制。在 MySQL 中，不同存储引擎使用不同的加锁方式；我们以 InnoDB 存储引擎为例介绍 MySQL 中的锁机制，其他存储引擎中的锁相对简单一些。\n锁（Locking）是数据库在并发访问时保证数据一致性和完整性的主要机制。在 MySQL 中，不同存储引擎使用不同的加锁方式；我们以 InnoDB 存储引擎为例介绍 MySQL 中的锁机制，其他存储引擎中的锁相对简单一些。\n锁（Locking）是数据库在并发访问时保证数据一致性和完整性的主要机制。在 MySQL 中，不同存储引擎使用不同的加锁方式；我们以 InnoDB 存储引擎为例介绍 MySQL 中的锁机制，其他存储引擎中的锁相对简单一些。\n锁（Locking）是数据库在并发访问时保证数据一致性和完整性的主要机制。在 MySQL 中，不同存储引擎使用不同的加锁方式；我们以 InnoDB 存储引擎为例介绍 MySQL 中的锁机制，其他存储引擎中的锁相对简单一些。\n锁（Locking）是数据库在并发访问时保证数据一致性和完整性的主要机制。在 MySQL 中，不同存储引擎使用不同的加锁方式；我们以 InnoDB 存储引擎为例介绍 MySQL 中的锁机制，其他存储引擎中的锁相对简单一些。\n锁（Locking）是数据库在并发访问时保证数据一致性和完整性的主要机制。在 MySQL 中，不同存储引擎使用不同的加锁方式；我们以 InnoDB 存储引擎为例介绍 MySQL 中的锁机制，其他存储引擎中的锁相对简单一些。"
      },
      comments: [],
      toAdd: ""
    }
  },
  mounted:function () {
    //当组件一加载就执行的函数
    this.init()
  },
  methods:{
    init: function () {
      var that = this
      that.comments.push({
        user: "zsj.python之路",
        article_id: this.$route.params.id,
        date: "2019-12-2",
        content: "优秀"
      })
      that.comments.push({
        user: "zsj.python之路",
        article_id: this.$route.params.id,
        date: "2019-12-2",
        content: "优秀"
      })
      var nid = this.$route.params.id  //获取id
      var that = this
      this.$axios.request({
        url:'https://localhost/article/' + nid,
        methods:'GET',
        responseType:'json'
      }).then(function (response) {
        console.log(response)
        that.article = response.data;
      })

      this.$axios.request({
        url:'https://localhost/article/' + nid + '/comments',
        methods:'GET',
        responseType:'json'
      }).then(function (response) {
        console.log(response)
        that.comments = response.data;
      })
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.main {
  width: 1000px;
  box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);
  margin: auto;
  margin-bottom: 100px;
}
.extra {
  bottom: 10px;
  height: 20px;
  font-size: 12px;
}
.author {
  height: 20px;
  float: left;
  margin-left: 20px; 
  line-height: 20px;
  color:#909399;
}
.date {
  height: 20px;
  float: left;
  margin-left: 25px; 
  line-height: 20px;
  color:#C0C4CC;
}
.content {
  margin: auto;
  margin-top: 10px;
  margin-bottom: 10px;
  border-top: 1px solid #DCDFE6;
  border-bottom: 1px solid #DCDFE6;
  width: 960px;
  text-align: left;
  color: #606266
}
.comments {
  width: 940px;
  margin: auto;
}
.header {
  height: 20px;
}
.header .author {
  color: black;
  font-weight: bold;
  font-size: 14px;
  margin-left: 0px;
}
.header .date {
  font-size: 12px;
}
.comment {
  margin-top: 20px;
  margin-left: 20px;
  text-align: left;
  color: #606266
}
.comments li {
  padding: 8px;
  border-top: 1px dashed #DCDFE6;
}
.comments li:first-child {
  border-top: 1px #DCDFE6;
}
.addComment {
  height: 70px;
}
.el-button {
  float: right;
  margin-top: 10px;
}
</style>