<template>
  <view class="container">
    <!-- 轮播图部分 -->
    <swiper class="swiper" 
	:indicator-dots="true"
	:autoplay="true" 
	:interval="3000" 
	:circular="true" 
	:duration="1000"
	indicator-color="#fff" 
	indicator-active-color="#f00">
      <swiper-item v-for="(item, index) in swiperList" :key="index">
        <image :src="item.image" mode="aspectFill"></image>
      </swiper-item>
    </swiper>
    
  <view class="title">
    西安历史名胜
  </view>
  <view class="history-list">
    <!-- <view class="item">
      <view class="img">
        <image src="/static/images/h1.jpg" mode="scaleToFill"></image>
      </view>
      <view class="text">秦兵马俑</view>
    </view> -->
   <!-- <view class="item">
      <view class="img">
        <image src="/static/images/h1.jpg" mode="scaleToFill"></image>
      </view>
      <view class="text">秦兵马俑</view>
    </view> -->
  </view>
  </view>
  
  <view class="history-list">
  			<view class="item" v-for="(item,index) in historys" :key="index" @tap="toDetails(index)">
  				<view class="img">
  					<image :src="item.pic" mode="scaleToFill"></image>
  				</view>
  				<view class="text">{{item.name}}</view>
  			</view>
  			 
  		</view>
</template>



<script setup>
import { ref } from 'vue'

const swiperList = ref([
  { image: '/static/images/hsw1.jpg' },
  { image: '/static/images/hsw2.jpg' },
  { image: '/static/images/hsw3.jpg' },
  { image: '/static/images/hsw4.jpg' },
  { image: '/static/images/hsw5.jpg' },
  { image: '/static/images/hsw6.jpg' }
])
	const historys=ref([
		{name:'秦兵马俑',pic:'/static/images/h1.jpg'	},
		{name:'大雁塔',pic:'/static/images/h2.jpg'},
		{name:'明城墙',pic:'/static/images/h3.jpg'},
		{name:'华清池',pic:'/static/images/h4.jpg'},
		{name:'明钟楼',pic:'/static/images/h5.jpg'},
		{name:'历史博物馆',pic:'/static/images/h6.jpg'},
		{name:'大唐芙蓉园',pic:'/static/images/h7.jpg'},
		{name:'大唐不夜城',pic:'/static/images/h8.jpg'},
		{name:'回民巷',pic:'/static/images/h9.jpg'},
		{name:'永兴坊',pic:'/static/images/h10.jpg'}	 
	])

const toDetails = (index) => {
  uni.navigateTo({
    url: `/pages/historyDetails/historyDetails?index=${index}`
  })
}
</script>

<style>
.container {
  width: 100%;
}

.swiper {
  width: 100%;
  height: 400rpx;
}

.swiper image {
  width: 100%;
  height: 100%;
}

.title {
  font-size: 36rpx;
  font-weight: bold;
  padding: 20rpx;
  color: #333;
  text-align: center;
}

.history-list {
  padding: 20rpx;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

.history-list .item {
  width: 48%;
  margin-bottom: 20rpx;
  background: #fff;
  border-radius: 10rpx;
  overflow: hidden;
  box-shadow: 0 2rpx 10rpx rgba(0,0,0,0.1);
}

.history-list .item .img {
  width: 100%;
  height: 200rpx;
}

.history-list .item .img image {
  width: 100%;
  height: 100%;
}

.history-list .item .text {
  padding: 10rpx;
  text-align: center;
  font-size: 28rpx;
  color: #333;
}
</style>
