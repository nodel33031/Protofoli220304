<template>
  <div class="header mb-3 " style="background-color:black;">
    <div class="nav">
      <a
      ><img src="../assets/LOGO_210623.jpg" alt=""  style="width:100px;height:100px"/></a>
      <div style="margin:auto"><router-link to="/" >登出</router-link>  </div>
    </div>

  </div>
  <div class="">
    <vue3VideoPlay
      width="900px"
      height="600px"

      title="柳吟影片"
      :src="options.src"
      :type="options.type"
      :autoPlay="false"
    />
    
  </div>
  <div class="footer" style="background-color:black">
    <div class="footerrow" >
      <a
        ><img src="../assets/LOGO_210623.jpg" alt=""  style="width:100px;height:100px"/></a>
    </div>
    <p class="footerlast">Copyright © 2021 戰狼集團 All Rights Reserved.</p>
  </div>
</template>
<script setup>
import { reactive } from "vue";

const options = reactive({
  width: "1000px", //播放器高度
  height: "520px", //播放器高度
  color: "#409eff", //主题色
  currentTime: 60,
  speed: false, //关闭进度条拖动
  title: "", //视频名称
  src: "http://192.168.0.20:8000/video/play/212?type=m3u8&fileName=test.m3u8", //视频源
  type: "m3u8",
});
</script>
<style>
.footer {
  background-color: #000000;
  height: 200px;
  margin-top: 50px;
  text-align: left;
  padding: 40px;
}
.footerlast {
  color: white;
}
#refPlayerWrap {
  margin: auto;
}
.header {
  padding:50px 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.header img {
  width: 223px;
  height: 60px;
  padding-left: 15px;
}
.container {
  height: 100%;
  text-align: center;
  background-color: #4d4a4a;  
}


</style>
