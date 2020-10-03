<template>
  <div id="home">
    <NavBar class="home-bar">
      <div slot="center">购物车</div>
    </NavBar>

  </div>
</template>

<script>
import NavBar from "@/components/common/navbar/NavBar";

import {getHomeMultidata} from "@/network/home";


export default {
  name: "Home",
  components: {
    NavBar,
  },
  data() {
    return {
      banner: [],
      recommend: [],
    }
  },
  created() {
    this.getHomeMultidata()
  },
  methods: {

    /*
    * 网络请求相关的内容
    * */
    getHomeMultidata() {
      getHomeMultidata().then(res => {
        console.log(res);
        this.banner = res.data.data.banner.list
        this.recommend = res.data.data.recommend.list
      })
    }

  }
}
</script>

<style scoped>
.home-bar {
  background-color: var(--color-tint);
  color: #fff;
}

.my-swipe .van-swipe-item {
  color: #fff;
  font-size: 20px;
  line-height: 150px;
  text-align: center;
  background-color: #39a9ed;
}
</style>
