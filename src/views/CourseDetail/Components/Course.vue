<template>
  <div class="c_wapper">
    <div class="course">
      <div class="l_img">
        <img :src="videoInfo.cover_img" :title="videoInfo.title" />
      </div>
      <div class="r_txt">
        <div class="txt">
          <span>综合评分:</span>
          <p>{{videoInfo.point}}</p>
        </div>
        <div class="txt">
          <span>价格:</span>
          <p>￥ {{videoInfo.price /100}}</p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  //从父组件传内容过来
  props: {
    videoInfo: {
      type: Object,
      required: true
    }
  }
};
</script>

<style lang="scss" scoped>
//包裹层
.c_wrapper {
  padding:50 50 50 50px;
}
//视频信息包裹层
.course {
  margin: 14px 0;
  display: flex; //设置flex，左右布局
}
//视频左边图⽚片层
.l_img {
  height: 300px;
  margin-right: 14px;
  & img {
    height: 100%;
    border-radius: 15px;
  }
}
// 视频右边⽂文字包裹层
.r_txt {
  padding: 6px 0;
  font-size: 12px;
  flex: 1; //设置1可⾃自动伸缩占⽤用剩余空间
}
//每⾏行行⽂文字层（综合评分、价格）
.txt {
  // 设置flex让⽂文字两端对⻬齐
  display: flex;
  justify-content: space-between;
  line-height: 40px;
  & p {
    text-align: center;
    width: 40%;
    color: #3bb149;
  }
  & i {
    color: #666;
    font-weight: bolder;
    width: 60%;
    & span {
      color: #2b333b;
      font-size: 12px;
    }
  }
}
</style>