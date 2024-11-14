<template>
	<view class="content">
		<!-- 顶部图片轮播 -->
		<swiper class="banner-swiper" 
			:indicator-dots="true" 
			:autoplay="true" 
			:interval="3000" 
			:circular="true" 
			:duration="1000"
			indicator-color="#fff" 
			indicator-active-color="#f00">
			<swiper-item v-for="(item, index) in bannerList" :key="'banner'+index">
				<view class="swiper-item">
					<image :src="item.img" mode="widthFix"></image>
				</view>
			</swiper-item>
		</swiper>
<view class="title">
    长安美食
  </view>
		<!-- 顶部美食导航 -->
		<view class="food-nav">
			<view class="nav-item" 
				v-for="(item, index) in foodsList" 
				:key="index"
				:class="{ active: tabIndex === index }"
				@click="changeTab(index)">
				{{ item.name }}
			</view>
		</view>

		<!-- 美食详情轮播 -->
		<swiper class="food-swiper" 
			:current="tabIndex" 
			@change="handleSwiperChange" 
			:indicator-dots="false" 
			:autoplay="false">
			<swiper-item v-for="(item, index) in foodsList" :key="index">
				<view class="food-detail">
					<image :src="item.img" mode="widthFix"></image>
					<view class="food-info">
						<view class="food-name">{{item.name}}</view>
						<view class="food-intro">{{item.intro}}</view>
					</view>
				</view>
				
			</swiper-item>
		</swiper>
	</view>
	
</template>

<script setup>
import { ref } from 'vue'

const tabIndex = ref(0)

// 顶部轮播图数据
const bannerList = ref([
	{ img: "/static/images/food1.jpg" },
	{ img: "/static/images/food4.jpg" },
	{ img: "/static/images/food5.jpg" },
	{ img: "/static/images/food6.jpg" },
	{ img: "/static/images/food7.jpg" },
	{ img: "/static/images/food8.jpg" }
])

// 添加loading状态管理
const isLoading = ref(false)

// 美食列表数据
const foodsList = ref([
	{
		name: '西安凉皮',
		img: "/static/images/f01.jpg",
		intro: '西安凉皮是陕西省西安市的一种特色小吃。西安市面上的凉皮大概分三种：岐山擀面皮、汉中热面皮和秦镇米面凉皮。其中以岐山擀面皮最受欢迎。因为擀面皮是从唐代冷淘面演变而来，其面皮选料精良，工艺严谨，调味讲究，以“白、薄、光、软、筋、香”而闻名，凉爽可口，具有筋斗、柔软、凉香、酸辣可口、四季皆宜之特点。在古代，擀面皮乃是给宫里的御供食品，故西府人又称擀面皮为“御京粉'
	},
	{
		name: '羊肉泡馍',
		img: "/static/images/f02.jpg",
		intro: '羊肉泡馍是陕西省西安市的一道传统美食，该菜品烹制精细，料重味醇，肉烂汤浓，肥而不腻，营养丰富，香气四溢，诱人食欲，食后回味无穷。因它暖胃耐饥，素为西安和西北地区各族人民所喜爱，外宾来陕也争先品尝，以饱口福。新中国成立以来，特别是近年来用以招待国际友人，也深受好评。羊肉泡馍已成为陕西名食的“总代表”。'
	},
	{
		name: '臊子面',
		img: "/static/images/f03.jpg",
		intro: '臊子面是中国陕西省的特色传统面食之一、是著名西府小吃，以宝鸡的岐山臊子面最为正宗。在陕西关中平原及甘肃陇东等地方流行。臊子面历史悠久，其中含有配菜比如豆腐，鸡蛋等，做法简单。臊子就是肉丁的意思。对于陕西人来说，臊子面的配色尤为重要，黄色的鸡蛋皮、黑色的木耳、红色的胡萝卜、绿色的蒜苗、白色的豆腐等材料，既好看又好吃。'
	},
	{
		name: '葫芦鸡',
		img: "/static/images/f04.jpg",
		intro: '葫芦鸡是陕西西安市汉族传统名菜，始于唐代。葫芦鸡的制作分清煮、蒸笼、油炸三道工序。金黄美味的葫芦鸡，随即盛盘中，上桌时另带小碟花椒盐佐食。 色泽金红，皮酥肉嫩，香烂味醇，筷到骨脱。含有丰富蛋白质和人体所需的饱和脂肪酸。正宗的葫芦鸡外酥里嫩，表皮金黄诱人，吃起来香醇软烂，真正是筷到骨脱，令人回味无穷，因而也被誉为“长安第一味”。'
	},
	{
		name: '肉夹馍',
		img: "/static/images/f05.jpg",
		intro: '“天下美食，唯肉夹馍不朽。”一口咬下，先是面饼的松软，再是腊汁肉的肥而不腻，最后是香菜和辣椒的爽口清香。这三种截然不同的口感在口中交融，仿佛味蕾上的芭蕾舞，让人陶醉其中。肉夹馍的历史，可追溯至汉代。当时，肉夹馍被称为“馍夹肉”。到了唐朝，肉夹馍已成为宫廷宴席上的佳肴。宋朝时候，肉夹馍更是风靡一时，成为了民间百姓喜爱的美食之一。如今，肉夹馍已经传遍世界各地，成为了中华美食文化的重要组成部分。'
	}
])

// 优化切换函数，添加加载状态
const changeTab = async (index) => {
	isLoading.value = true
	try {
		tabIndex.value = index
	} finally {
		isLoading.value = false
	}
}

// 优化轮播切换处理
const handleSwiperChange = (e) => {
	const { current } = e.detail
	tabIndex.value = current
}
</script>

<style>
.content {
	height: 100vh;
	display: flex;
	flex-direction: column;
}

/* 顶部轮播图样式 */
.banner-swiper {
	height: 300rpx;
}

.swiper-item image {
	width: 100%;
	height: 100%;
}

.food-nav {
	display: flex;
	padding: 20rpx;
	background-color: #fff;
	border-bottom: 1rpx solid #eee;
}

.nav-item {
	flex: 1;
	text-align: center;
	padding: 20rpx 0;
	font-size: 28rpx;
	color: #333;
	position: relative;
}

.nav-item.active {
	color: #f00;
	font-weight: bold;
	transition: all 0.3s ease;
}

.nav-item.active::after {
	content: '';
	position: absolute;
	bottom: 0;
	left: 50%;
	transform: translateX(-50%);
	width: 40rpx;
	height: 4rpx;
	background-color: #f00;
}

.food-swiper {
	flex: 1;
	height: 0;
}

.food-detail {
	height: 100%;
	padding: 20rpx;
}

.food-detail image {
	width: 100%;
	border-radius: 10rpx;
	transition: opacity 0.3s ease;
}

.food-info {
	padding: 30rpx;
	background: #fff;
	border-radius: 10rpx;
	margin-top: -40rpx;
	position: relative;
	box-shadow: 0 2rpx 10rpx rgba(0,0,0,0.1);
}

.food-name {
	font-size: 36rpx;
	font-weight: bold;
	margin-bottom: 20rpx;
}

.food-intro {
	font-size: 28rpx;
	color: #666;
	line-height: 1.6;
}
	.title {
		text-align: center;
		margin: 20rpx;
		font-size: 40rpx;
		color: #888;
	}

/* 添加加载状态样式 */
.loading {
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
}

/* 添加响应式布局支持 */
@media screen and (min-width: 768px) {
	.food-nav {
		max-width: 960px;
		margin: 0 auto;
	}
	
	.food-detail {
		max-width: 960px;
		margin: 0 auto;
	}
}
</style>