<template>
  <view class="about-page">
    <view class="header">
      <image class="logo" :src="logoUrl" mode="aspectFit"></image>
      <text class="title">关于此软件</text>
    </view>
    <view class="content">
      <text class="description">这是一个及其简约的课程表软件，基于uni-app框架开发。</text>
      <view class="author-info">
        <view class="info-row">
          <text class="author-name">作者: 张鹏宇</text>
        </view>
        <view class="info-row">
          <text class="author-name">部分数据支持: 张敬伟</text>
        </view>
        <view class="info-row">
          <text class="author-email">反馈邮箱: wwei50057@gmail.com</text>
        </view>
        <view class="info-row">
          <text class="author-github">GitHub: <a :href="githubUrl" target="_blank">Mst7we1</a></text>
        </view>
      </view>
    </view>
    <component-global-tab-bar></component-global-tab-bar>
  </view>
</template>

<script>
import ComponentGlobalTabBar from '@/components/TabBar.vue';

export default {
  components: {
    ComponentGlobalTabBar
  },
  data() {
    return {
      logoUrl: '../../static/logo.png',
      githubUrl: 'https://github.com/Mst7we1'
    };
  }
};
</script>

<style scoped>
.about-page {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  background-color: #f5f5f5;
  padding: 20rpx;
}

.header {
  display: flex;
  align-items: center;
  margin-bottom: 20rpx;
  padding: 10rpx 0;
  border-bottom: 1rpx solid #ccc;
}

.logo {
  width: 80rpx;
  height: 80rpx;
  margin-right: 20rpx;
  border-radius: 50%; /* 圆角 */
  box-shadow: 0 2rpx 4rpx rgba(0, 0, 0, 0.1); /* 添加阴影 */
  transition: transform 0.3s ease-in-out;
  cursor: pointer;
}

.logo:hover {
  transform: scale(1.1); /* 鼠标悬停时放大图标 */
}

.title {
  font-size: 36rpx;
  font-weight: bold;
  color: #333;
}

.content {
  flex-grow: 1;
  margin-bottom: 100rpx; /* 为底部导航栏预留空间 */
}

.description {
  margin-bottom: 20rpx;
  font-size: 30rpx;
  color: #333;
  line-height: 1.5;
}

.author-info {
  margin-top: 20rpx;
  font-size: 28rpx;
  color: #333;
}

.info-row {
  display: flex;
  align-items: center;
  margin-bottom: 10rpx;
}

.author-name {
  font-weight: bold;
  color: #333;
}

.author-email {
  color: #666;
}

.author-github {
  color: #333;
}

.author-github a {
  color: #333;
  text-decoration: none;
}

.author-github a:hover {
  text-decoration: underline;
}

/* 底部导航栏 */
.fixed-tab-bar {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  height: 100rpx; /* 根据实际需要调整高度 */
  background-color: #f5f5f5;
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
  transition: transform 0.3s ease-in-out; /* 添加过渡动画 */
}

.tab-item:hover image {
  transform: scale(1.1); /* 鼠标悬停时放大图标 */
}
</style>