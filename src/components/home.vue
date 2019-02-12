<template>
  <div id="home">
    <div class="topbar">
      <img src="./menu.png" alt class="menu">
      <span class="topspan" @click="request">点击我{{name}}</span>
      <img src="./bell.png" alt class="notify">
      <img src="./more.png" alt class="more">
    </div>
    <div class="hotstory">
      <div class="box">
        <div class="item">1</div>
        <div class="item">2</div>
        <div class="item">3</div>
        <div class="item">4</div>
        <div class="item">5</div>
      </div>
    </div>
    <div>
      Git Hub ID:
      <input type="text" v-model="uid">
      <button @click="getUserMessage(uid)">获取指定用户名信息</button>
      <p>{{message.node_id}}</p>
      <p>{{message.avatar_url}}</p>
      <!-- 绑定图片到控件 -->
      <img :src="message.avatar_url" alt>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      name: "",
      hotstory: [],
      allstory: [],
      user: {
        name: "输入姓名",
        age: "30"
      },
      message: {},
      uid: "",
      getUser: ""
    };
  },
  methods: {
    request() {
      // axios
      //   .get("api1", { params: { name: "名字11", gender: "112233" }})//值放在括号里
      //   .then(rsp => {
      //     console.log(rsp.data.name);
      //     this.name = rsp.data.name;
      //   })
      //   .catch(erro => {
      //     console.log(erro);
      //   });

      // axios.post('api1','name=键值对输入&age=30')//方式1
      axios
        .post("api1", this.user, {
          transformRequest: [
            data => {
              let params = "";
              for (let index in data) {
                params += index + "=" + data[index] + "&";
              }
              return params;
            }
          ]
        }) //方式2
        .then(rsp => {
          console.log(rsp.data);
          this.name = rsp.data.name;
        });
    },
    getUserMessage(uid) {
      axios.get("https://api.github.com/users/" + uid).then(rsp => {
        console.log(rsp.data);
        this.getUser = rsp.data.node_id;
        this.message = rsp.data; //空json接收
      });
    }
  }
  // mounted() {// (rsp)=>{} es6语法等同于 function(rsp){}
  // //axios使用的插件
  //   request:data=>{
  //   }
  //   axios
  //     .get('api1')
  //     .then(rsp => {
  //       console.log(rsp.data.name);
  //       this.name=rsp.data.name;
  //     })
  //     .catch(erro => {
  //       console.log(erro);
  //     });
  // }
};
</script>
<style scoped>
.topbar {
  width: 100%;
  height: 50px;
  background-color: #00a2ed;
  position: relative;
}
.topbar img {
  width: 30px;
  height: 30px;
  position: absolute;
  top: 0;
  bottom: 0;
  margin: auto, 0;
}
.topbar .more {
  right: 20px;
  margin: auto;
}
.topbar .notify {
  right: 60px;
  margin: auto;
}
.menu {
  left: 20px;
  margin: auto;
}
.topspan {
  position: absolute;
  left: 50%;
  margin: 0, auto;
  font-size: 1.25em;
  color: white;
  top: 20%;
}
.hotstory {
  width: 100%;
  height: 200px;
  background-color: #ccc;
  position: relative;
  overflow: hidden;
}
.hotstory .box {
  width: 500%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  animation: loop 20s linear infinite;
}
.hotstory .box .item {
  width: 20%;
  height: 100%;
  float: left;
}
@keyframes loop {
  0%,
  19%,
  100% {
    transform: translate(0, 0);
  }
  20%,
  39% {
    transform: translate(-20%, 0);
  }
  40%,
  59% {
    transform: translate(-40%, 0);
  }
  60%,
  79% {
    transform: translate(-60%, 0);
  }
  80%,
  99% {
    transform: translate(-80%, 0);
  }
}
</style>


