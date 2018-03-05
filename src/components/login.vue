<template>
  <div id="login">
    <label for="">用户名：</label>
      <input type="text" placeholder="请输入用户名" v-model="username">
    <label for="">密码：</label>
      <input type="password" placeholder="请输入密码" v-model="password">
    <a class="btn" @click="doLogin">登录</a>{{ error }}

  </div>
</template>

<script>
  export default {
    name: 'login',
    data() {
      return {
        username: '',
        password: '',
        error: '',
      }
    },
    methods:{
      doLogin(){
        console.log(this);
        var that = this;
        this.$axios.request({
          url: 'http://52.15.206.110:8080/api/login',
          method: 'POST',
          data: {
            username: this.username,
            password: this.password
          },
          responseType: 'json'
        }).then(function (response) {
          console.log(response);
          // 登录成功之跳转到首页
          that.$router.push('/index')
        }).catch(function (error) {
          console.log(error);
          // 登录失败在页面显示失败信息
          that.error = error.data
        })
      }
    }
  }
</script>
