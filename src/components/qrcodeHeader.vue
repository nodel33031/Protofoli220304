<template>
    <div class="logo mb-3" style="background-color:black">
        <img src="../assets/LOGO_210623.jpg" alt="">
    <div id="nav">
        <router-link style="color:white" to="/qrcodeMain">QRcode產生器</router-link> |
        <router-link style="color:white" to="/qrcodeMain2">影片管理系統</router-link> |
        <router-link style="color:white" to="/" >登出</router-link>        
    </div>        
    </div>

</template>
<style >
.logo{
    width: 100%;
    display: flex;
}

.logo img{ 
    /* width:100%; */
    height: 80px;
    margin: 15px;
}
#nav{
    margin: auto;
}
</style>