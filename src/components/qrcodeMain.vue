<template>
  <Header></Header>
  <Searchmodal v-on:sureMovie="emitMain"></Searchmodal>
  <form action="">
    <div class="container" style="padding-bottom: 12rem">
      <div class="row">
        <div class="col">
          <!-- Content here -->
          <div>User {{ $route.params.id }}</div>
          <h2>選擇QR code網址產生方式</h2>
          <div class="radio d-flex pb-3">
            <div class="form-check pe-5 fs-3">
              <input
                class="form-check-input"
                type="radio"
                name="flexRadioDefault"
                id="flexRadioDefault1"
                v-on:click="selfmade()"
              />
              <label class="form-check-label" for="flexRadioDefault1">
                自訂名稱
              </label>
            </div>
            <div class="form-check fs-3">
              <input
                class="form-check-input"
                type="radio"
                name="flexRadioDefault"
                id="flexRadioDefault2"
                v-on:click="random()"
                checked
              />
              <label class="form-check-label" for="flexRadioDefault2">
                系統隨機
              </label>
            </div>
          </div>
          <div class="">
            <input
              class="w-100 main1input"
              id="input_text"
              name="input_text"
              type="text"
              placeholder="請輸入自訂名稱"
              v-model="webqrcode.imgUrl"
            />
            <h2 class="py-3">播放清單名稱</h2>
            <input
              id="playlist_name"
              class="w-100 main1input"
              name="playlist_name"
              type="text"
              placeholder="請輸入播放清單名稱(可不填)"
            />
          </div>
        </div>
        <div class="col">
          <div class="qrcode m-auto border">
            <img src="https://picsum.photos/300/300/?random=10" />
          </div>
          <div
            id="imgwebqrcode"
            style="
              background-color: rgb(211, 211, 211);
              width: 300px;
              margin: 0 auto;
            "
          >
            {{ "https://web.ly-edu.com.tw/to/" + webqrcode.imgUrl }}
          </div>
        </div>
      </div>
      <br />
      <div class="row">
        <h2>新增影片名稱</h2>
        <div class="col">
          <table class="table">
            <thead>
              <tr>
                <th>排序</th>
                <th>影片</th>
                <th>影片題目</th>
                <th>ID</th>
                <th></th>
              </tr>
            </thead>

            <tbody>
              <tr v-for="(item, i) in products" :key="item.id">
                <td>
                  <input
                    class="qrcodeformstyle1 main1input"
                    id="newVideoOrder1"
                    name="newVideoOrder1"
                    type="text"
                    placeholder="順序"
                    :value=" i + 1"
                     
                    
                  />
                </td>
                <td>
                  <input
                    class="qrcodeformstyle main1input"
                    id="newVideoName1"
                    name="newVideoName1"
                    type="text"
                    placeholder="請輸入影片名稱"
                    v-model="this.videoList.videos[i].videoName"
                  />
                </td>
                <td>
                  <input
                    class="qrcodeformstyle main1input"
                    id="newVideoName1"
                    name="newVideoName1"
                    type="text"
                    placeholder="請輸入影片題目"
                    v-model="this.videoList.videos[i].comment"
                  />
                </td>
                <td>
                  <input
                    class="qrcodeformstyle main1input"
                    id="newVideoName1"
                    name="newVideoName1"
                    type="text"
                    placeholder="請搜尋影片ID"
                    :value="(emitName[i] = this.videoList.videos[i].video_id)"
                  />
                  <!-- @input="item.movieID=$event.target.value" -->
                </td>
                <td>
                  <button
                    type="button"
                    class="btn btn-dark"
                    data-bs-toggle="modal"
                    data-bs-target="#exampleModal"
                  >
                    <i class="fa fa-search"></i>
                  </button>
                </td>
              </tr>
            </tbody>
          </table>
          <div style="text-align: left">
            <button
              type="button"
              v-on:click="addlist()"
              class="btn btn-dark me-2"
            >
              增加
            </button>
            <button type="button" v-on:click="del()" class="btn btn-dark">
              刪除
            </button>
            <br />
            <br />
            <input
              class="btn btn-dark"
              type="button"
              value="送出"
              v-on:click="onSubmit()"
            />
            <input type="text" name="Data1" style="display: none" />
            <input type="text" name="Data2" style="display: none" />
          </div>
        </div>
      </div>
    </div>
  </form>
  <Footer></Footer>
</template>
<style>
.qrcode {
  width: 300px;
  height: 300px;
}
.main1input {
  border: none;
  border-bottom: 1px solid #4f4f4f;
}
table .main1input {
  border-bottom: none;
  /* color: rgb(211, 211, 211); */
}
h2 {
  text-align: start;
}
</style>
<script>
import Header from "@/components/qrcodeHeader.vue";
import Searchmodal from "@/components/qrcodeSearchmodal.vue";
import Footer from "@/components/qrcodeFooter.vue";
const products = [{}];
export default {
  data() {
    return {
      videoList: {
        custom_url: null,
        playlist_name: null,
        videos: [
          {
            order: 1,
            videoName: null,
            comment: null,
            video_id: null,
          },
        ],
      },
      products: [{}],
      webqrcode: {
        imgUrl: "",
      },
      emitName: [],
    };
  },
  components: {
    Searchmodal,
    Header,
    Footer,
  },
  created() {
    this.products = products;
    this.webqrcode.imgUrl = _uuid();

    function _uuid() {
      let d = Date.now();
      if (
        typeof performance !== "undefined" &&
        typeof performance.now === "function"
      ) {
        d += performance.now(); //use high-precision timer if available
      }
      return "xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx".replace(
        /[xy]/g,
        function (c) {
          let r = (d + Math.random() * 16) % 16 | 0;
          d = Math.floor(d / 16);
          return (c === "x" ? r : (r & 0x3) | 0x8).toString(16);
        }
      );
    }
  },
  methods: {

    onSubmit() {
      console.log(this.$route.params.id);
      // let data1 = document.getElementsByTagName("input")[3].value
      // let data2 = document.getElementsByTagName("input")[4].value
      // const dataSend ={webUrl:data1,listName:data2}
      // console.log(this.products.length);
      // for(let i=5;i<5+this.products.length*4;i++){
      //   const listData = document.getElementsByTagName("input")[i].value
      //   // console.log(document.getElementsByTagName("input")[i].value);
      //   const allListdata ={listData:listData}
      //   // console.log(JSON.stringify(allListdata));
      //   document.getElementsByName("Data1").value=JSON.stringify(allListdata)
      //   console.log(document.getElementsByName("Data1").value);

      // }

      // document.getElementsByName("Data2").value=JSON.stringify(dataSend);
      // console.log(JSON.stringify(dataSend));
      // console.log(this.products[0].movieName);
      // this.abQrcode[0].imgUrl=document.getElementsByTagName("input")[3].value
      // this.abQrcode[0].listName=document.getElementsByTagName("input")[4].value
      // console.log(JSON.stringify(this.products));
      // console.log(JSON.stringify(this.abQrcode));
      console.log(JSON.stringify(this.videoList));
      console.log(this.videoList.videos.video_id);
    },
    addlist() {
      this.products.push({});
      this.videoList.videos.push({
        order: null,
        videoName: null,
        comment: null,
        video_id: null,
      });
    },
    del() {
      console.log(this.products.length);
      let index = this.products.length - 1;
      // const math =this.products.length-1
      if (this.products.length < 2) {
        this.emitName.splice(index, 1);
        alert("無新增欄位可以刪除");
        return;
      }
      this.products.pop();
      this.emitName.splice(index, 1);
    },
    selfmade() {
      // console.log(this.webqrcode.imgUrl);
      document.getElementById("input_text").value = "";
      document.getElementById("imgwebqrcode").innerText = "";
    },
    random() {
      document.getElementById("input_text").value = this.webqrcode.imgUrl;
      document.getElementById("imgwebqrcode").innerText =
        "https://web.ly-edu.com.tw/to/" + this.webqrcode.imgUrl;
    },
    emitMain(data) {
      console.log(data);
      this.emitName.push(data);
    },
  },
};
</script>
