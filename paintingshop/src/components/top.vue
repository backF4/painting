<template>
  <div id="app">
    <el-menu :default-active="activeIndex" class="el-menu-demo" mode="horizontal" @select="handleSelect"
      background-color="#545c64" text-color="#fff" active-text-color="#ffd04b">
      <el-menu-item index="1">
        <router-link to="/">画丹手商城</router-link>
      </el-menu-item>
      <el-menu-item index="2" v-show="$store.getters.loginstatus==true">欢迎{{$store.getters.userAccount}}</el-menu-item>
      <el-menu-item index="3">
        <router-link to="/regist" v-show="!($store.getters.userType==1||$store.getters.userType==2)">注册</router-link>
      </el-menu-item>
      <el-menu-item index="4">
        <router-link to="/login" v-show="!($store.getters.userType==1||$store.getters.userType==2)">登录</router-link>
      </el-menu-item>
      <div class="right1">
        <el-menu-item index="5">
          <a>消息通知</a>
        </el-menu-item>
        <el-menu-item index="6" v-show="$store.getters.userType==1">
          <router-link to="/myorder">我的订单</router-link>
        </el-menu-item>
        <el-menu-item index="7" v-show="$store.getters.userType==1">
          <router-link to="/mycar">购物车</router-link>
        </el-menu-item>
        <el-menu-item index="9" v-show="$store.getters.userType==2">
          <router-link to="/echarts">统计</router-link>
        </el-menu-item>
        <el-menu-item index="10" v-show="$store.getters.userType==2">
          <router-link to="/release">发布商品</router-link>
        </el-menu-item>
        <el-menu-item index="8" v-on:click="logout" v-show="$store.getters.userType==2||$store.getters.userType==1">
          <a>注销</a>
        </el-menu-item>
      </div>
    </el-menu>
  </div>
</template>

<script>
  // @ is an alias to /src
  export default {
    name: "app",
    data: function () {
      return {
        // myregist: true,
        // mylogin: true,
        activeIndex: "1",
        activeIndex2: "1"
      };
    },
    methods: {
      
      handleSelect(key, keyPath) {
        console.log(key, keyPath);
      },
      logout: function () {
        // console.log(this.$store.getters.userType);
        this.$store.commit("LoginOut", false);
        this.$router.push({
          path: "/"
        });
      }
      // @ is an alias to /src
    },
    components: {},
    created: function () {
      if (this.$router.path == "reg") {
        this.activeIndex2 = "7";
      }
    }
  };
</script>
<style>
  * {
    padding: 0;
    margin: 0;
  }

  #nav {
    padding: 0px;
  }

  el-menu-item {
    background-color: rgb(168, 114, 114);
  }

  #blank {
    width: 45%;
  }

  element.style {
    background-color: rgb(168, 114, 114);
  }

  .right1 {
    position: absolute;
    right: 10px;
    top: 3px;
    display: flex;
  }

  a {
    text-decoration: none;
    color: white;
  }
</style>