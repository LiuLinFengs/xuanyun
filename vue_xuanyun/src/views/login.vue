<template>
  <div class="login_style">
    <div>
      <img src="http://127.0.0.1:3000/img/footer/logo_03.png" alt />
      <ul class="login_list">
        <li>
          <router-link to="#" class="bar_login">登录</router-link>
        </li>
        <li>
          <router-link to="./reg" class="bar_reg">注册</router-link>
        </li>
        <li>
          <router-link to="/" class="bar_index">返回首页</router-link>
        </li>
      </ul>
    </div>
    <div class="login_bg">
      <div>
        <img src="http://127.0.0.1:3000/img/login/ziti_07.png" alt />
        <h4>炫云账号登录</h4>
        <el-input v-model="uname" placeholder="请输入用户名"></el-input>
        <el-input placeholder="请输入密码" v-model="upwd" show-password></el-input>
        <el-button style="width:100%" @click="login()">登录</el-button>
        <div>
          <router-link to="#" class="link_left">注册账户</router-link>
          <router-link to="#" class="link_right">忘记密码?</router-link>
        </div>
      </div>
    </div>
    <p>©2009-2016北京炫我科技有限公司 | 京ICP备13039808号</p>
  </div>
</template>
<script>
export default {
  data() {
    return {
      uname: "mm4521",
      upwd: "123456"
    };
  },
  methods: {
    login() {
      var uname = this.uname;
      var upwd = this.upwd;
      if (!uname || !upwd) {
        this.$alert("用户名或密码不能为空");
      } else {
        this.axios
          .get("/login", { params: { uname: uname, upwd: upwd } })
          .then(result => {
            console.log(result.data.code);
            if (result.data.code == 1) {
              this.$alert("登录成功", {
                showConfirmButton: false,
                showCancelButton: false,
                showClose: false
              });
              sessionStorage.setItem("name",uname);
              setInterval(() => {
                location.href = "/";
              }, 300);
            } else {
              this.$alert("用户名或密码错误");
            }
          });
      }
    }
  }
};
</script>
<style scoped>
a:hover {
  text-decoration: none;
}
.login_style {
  width: 100%;
  margin: 20px 0;
}
.login_style > div:first-child {
  width: 1400px;
  margin: 0 auto;
}
.login_list {
  list-style: none;
  float: right;
}
.login_list > li {
  float: left;
  margin: 0 25px;
  line-height: 38px;
}
.login_bg {
  height: 560px;
  background: url("http://127.0.0.1:3000/img/login/login_bj_03.jpg") no-repeat;
  background-position: 50%;
  text-align: center;
  position: relative;
  margin: 20px 0;
}
.login_bg > div {
  /* width: 500px; */
  text-align: center;
  position: absolute;
  top: 20%;
  left: 35%;
}
.login_bg > div > h4 {
  padding: 30px 0;
  color: #fff;
}
.el-input {
  margin: 10px 0 !important;
  border: 0;
}
.el-button {
  font-size: 16px;
  margin-top: 20px;
  border-radius: 0;
  border: 0;
}
.el-button:hover {
  background-color: #f00;
  border: 0;
  color: #fff;
}
.link_left,
.link_right {
  color: #fff;
  float: left;
  margin-top: 3px;
  font-size: 14px;
}
.link_right {
  float: right;
}
.link_left:hover,
.link_right:hover {
  color: blue;
}
.login_bg + p {
  text-align: center;
  font: 14px "微软雅黑";
}
.bar_login,
.bar_reg {
  color: black;
}
.bar_index {
  font-size: 16px;
  color: gray;
}
.bar_index:hover {
  color: black;
}
</style>