<template>
  <view class="fixed-tab-bar">
    <navigator class="tab-item" url="/pages/index/index">
      <image src="file:///D:/desktop/uni/大数据2301课程表/static/course_table.png" mode="aspectFit"></image>
     <!-- <text>课程表</text> -->
    </navigator>
    <navigator class="tab-item" url="/pages/index/about">
      <image src="file:///D:/desktop/uni/大数据2301课程表/static/about.png" mode="aspectFit"></image>
     <!-- <text>关于</text> -->
    </navigator>
  </view>
</template>

<script>
export default {
  // 组件逻辑
};
</script>

<style scoped>
.fixed-tab-bar {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  height: 100rpx; /* 根据实际需要调整高度 */
  background-color: #F8F8F8;
  display: flex;
  justify-content: space-around;
  align-items: center;
  box-shadow: 0 -1px 2px rgba(0, 0, 0, 0.1);
}

.tab-item {
  text-align: center;
  width: 50%;
}

.tab-item image {
  width: 50rpx;
  height: 50rpx;
}
</style>