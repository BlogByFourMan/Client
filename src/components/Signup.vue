<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  <div>
      <el-input v-model="userID" placeholder="用户名(6~18位英文字母、数字、下划线)" class='inputClass' @blur='userValidateCheck()'></el-input>
   </div>
   <span class='info' id='user'>{{userinfo}}</span>
   <br>
   <div>
      <el-input v-model="password" placeholder="密码(6~18位数字、大小写字母)" class='inputClass' type='password' @blur ='passwordCheck()'></el-input>
   </div>
   <span class='info' id='pswd'>{{pswdinfo1}}</span>
   <br>
   <div>
      <el-input v-model="passwordConfirm" placeholder="再次输入密码确认" class='inputClass' type='password' @blur='passwordValidateCheck()'></el-input>
   </div>
   <span class='info' id='pswd'>{{pswdinfo2}}</span>
   <br>
   <div>
      <el-input v-model="mail" placeholder="邮箱" class='inputClass' @blur='mailValidateCheck()'></el-input>
   </div>
   <span class='info' id='email'>{{emailinfo}}</span>
   <br>
   <div>
    <el-button type="primary" @click='clickJoin()'>注册</el-button>
  </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Sign up',
      userID: '',
      password: '',
      passwordConfirm: '',
      mail: '',
      userinfo: '',
      pswdinfo1: '',
      pswdinfo2: '',
      emailinfo: ''
    }
  },
  methods: {
    clickJoin: function () {
      var that = this
      this.$axios.request({
        url: 'http://localhost:8081/user/register',
        method: 'POST',
        data: JSON.stringify({
          username: 'this.userID',
          password: 'this.password'
        }),
        responseType: 'json'
      }).then(function (response) {
        console.log(response.data)
        if (!response.data.error) {
          that.$store.commit('saveToken', {
            username: that.userID,
            token: response.data.token
          })
          that.$router.push('/')
        } else {
          alert(response.data.error)
        }
      })
    },
    userValidateCheck: function () {
      if (!(/[0-9a-zA-Z_]{6,18}/.test(this.userID))) {
        this.userinfo = '用户名格式不正确'
      } else {
        this.userinfo = ''
      }
    },
    passwordCheck: function () {
      if (!(/[0-9a-zA-Z]{6,18}/.test(this.password))) {
        this.pswdinfo1 = '密码格式不正确'
      } else {
        this.pswdinfo1 = ''
      }
    },
    passwordValidateCheck: function () {
      if (this.password !== this.passwordConfirm) {
        this.pswdinfo2 = '两次密码输入不相同'
      } else {
        this.pswdinfo2 = ''
      }
    },
    mailValidateCheck: function () {
      if (/^([A-Za-z0-9_])+([A-Za-z0-9_])+\.([A-Za-z]{2,4})/.test(this.mail)) {
        this.emailinfo = ''
      } else {
        this.emailinfo = '邮箱格式不正确'
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
body{
  font-family: "Helvetica Neue",Helvetica,"PingFang SC","Hiragino Sans GB","Microsoft YaHei","微软雅黑",Arial,sans-serif;
}
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.inputClass{
  width:300px
}
</style>
