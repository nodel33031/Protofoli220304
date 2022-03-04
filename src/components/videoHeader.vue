<template>
    <div class="logo" style="background-color:black">
        <img src="../assets/LOGO_210623.jpg" alt="">
          <nav class="navbar navbar-expand-sm navbar-light px-2 " style="background-color:black">

    <ul class="navbar-nav" >
      <li class="nav-item" >
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
        
    </div>
    
</template>
<style lang="less">
.logo{
    // width: 100%;
    display: flex;
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