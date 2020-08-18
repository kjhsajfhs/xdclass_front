<template>
  <div>
    <home-banner :banners="banners"></home-banner>
    <video-list :videoList="VideoList"></video-list>
    <common-footer></common-footer>
  </div>
</template>

<script>
import HomeBanner from "./Component/Banner";
import VideoList from "./Component/VideoList";
import CommonFooter from "@/components/CommonFooter";
import { getBanner, getVideoList } from "@/api/getData.js";

export default {
  //注册组件
  components: {
    HomeBanner,
    VideoList,
    CommonFooter
  },
  data() {
    //声明数据源
    return {
      banners: [],
      VideoList: []
    };
  },
  //定义方法
  methods: {
    async getBannerData() {
      try {
        //获取轮播图列表
        const result = await getBanner();
        console.log(result);
        if (result.data.code == 0) {
          this.banners = result.data.data;
        }
      } catch (error) {
        console.log(error);
      }
    },
    async getVList() {
      try {
        //获取视频列表
        const result = await getVideoList();
        if (result.data.code == 0) {
          this.VideoList = result.data.data;
        }
      } catch (error) {
        console.log(error);
      }
    }
  },
  mounted() {
    //页面渲染王朝调用方法
    this.getBannerData();
    this.getVList();
  }
};
</script>
<style lang="less" scoped>
</style>