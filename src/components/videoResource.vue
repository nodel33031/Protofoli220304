<template>
  <nav class="navbar navbar-expand-sm navbar-light px-2" style="background-color:black">
    <div class="logo">
      <img src="../assets/LOGO_210623.jpg" alt="" />
    </div>    
    <ul class="navbar-nav ms-auto mb-lg-0">
      <li class="nav-item">
        <router-link
          to="/videoMain/videolist_handout"
          id="prevent_header"
          class="m-3"
          >互動講義</router-link
        >
      </li>
      <li class="nav-item">
        <router-link to="/videoResource" id="prevent_header" class="m-3"
          >素材總管</router-link
        >
      </li>
      <li class="nav-item">
        <router-link
          to="/videoMemberplace/videoEditinfo"
          id="prevent_header"
          class="m-3"
          >會員中心</router-link
        >
      </li>
      <li class="nav-item">
        <router-link to="/" id="prevent_header" class="m-3">登出</router-link>
      </li>
    </ul> 
  </nav>
  <div class="bg-light px-3" style="height:59px"></div>
  <div class="container" style="padding-bottom:400px">
  <div style="position: static; text-align: right; " class="my-2">
      <input
        type="text"
        class="form-control"
        placeholder="講義名稱"
        aria-label="Recipient's username"
        aria-describedby="button-addon2"
        style="display:inline-block;max-width:20rem"
      />
      <button
        class="btn btn-outline-secondary"
        type="button"
        id="button-addon2"
        @click="setDatabase()"
      >
        查詢
      </button>
      <div style="min-width:150px;display:inline-block">
      
    <div class="btn btnBlue mx-2">建立目錄</div>
    <div class="btn btnBlue">上傳講義</div>
      </div>
  </div>
  <div class="row bg-light">
    <div class="col-1">
      <p></p>
    </div>
    <div class="col-3">
      <div class="py-3">講義名稱</div>
    </div>
    <div class="col-1">
      <div class="py-3">大小</div>
    </div>
    <div class="col-4">
      <div class="py-3">線上使用</div>
    </div>
    <div class="col-2">
      <div class="py-3">其他功能</div>
    </div>
  </div>
  <div
    class="row"
    v-for="item in database"
    :key="item.id"
    style="cursor: pointer"
  >
    <div class="col-1">
      <!-- <p>{{ item.fileName }}</p> -->      
    </div>
    <div class="col-1 p-1"> 
      <!-- <img src="../assets/png.png" style="width:40px;height:40px" alt=""> -->
      <img :src="setDatabase(item.directory,item.fileName)" style="width:40px;height:40px" alt="">
    </div>
    <div class="col-2 p-1">      
      <p>{{ item.fileName }}</p>        
    </div>
    <div class="col-1 p-1">
      <!-- <p>{{ item.state }}</p> -->
    </div>
    <div class="col-4 p-1">
      <!-- <p>{{ item.state }}</p> -->
    </div>
    <div class="col-2 p-1">
      <!-- <p>{{ item.state }}</p> -->
    </div>
  </div>
  </div> 
  <Footer></Footer>
</template>
<script>
import Footer from "../components/qrcodeFooter.vue" 
export default {
    data(){
        return{

        };

    },
    components:{
      Footer
    },
    methods:{
    videoMain(){
        window.location.href='/videoMain/videolist_handout';
      },
    videoMemberplace(){
        window.location.href='/videoMemberplace/videoEditinfo';
     },


    },
}
</script>
<style lang="less">
.btnBlue {
  background: rgb(255, 255, 255);
  color: #000000;
  border: 2px solid #000000;
  &:hover {
    border: 2px solid #000000;
    border-radius: 5px;
    background: #000000;
    color: #fff;    
    
  }
}
.logo img{ 
    /* width:100%; */
    height: 80px;
    margin: 15px;
}
#prevent_header {
  text-decoration: none;
  color: #ffffff;
  font-weight: 600;
  font-size: 18px;
  background-image: linear-gradient(#000000, #e6e6e6);
  background-position: left bottom;
  background-size: 0 2.5px;
  background-repeat: no-repeat;
  transition: background-size 0.5s;
  &:hover {
    background-size: 100% 2.5px;
  }
}

  
</style>