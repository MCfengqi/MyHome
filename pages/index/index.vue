<template>
	<!-- 轮播  -->
	<view class="content">
		<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :circular="true" :duration="1000"
			indicator-color="#fff" indicator-active-color="#f00">
			<swiper-item>
				<view class="swiper-item">
					<image src="../../static/images/xian1.jpg" mode="widthFix"></image>
				</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper-item">
					<image src="../../static/images/xian2.jpg" mode="widthFix"></image>
				</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper-item">
					<image src="../../static/images/xian3.jpg" mode="widthFix"></image>
				</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper-item">
					<image src="../../static/images/xian4.jpg" mode="widthFix"></image>
				</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper-item">
					<image src="../../static/images/xian5.jpg" mode="widthFix"></image>
				</view>
			</swiper-item>
		</swiper>
	</view>

	<!-- logo -->
	<view class="logo">
		<image src="../../static/logo.png" mode="widthFix"></image>
	</view>

	<!-- 长安八景  -->
	<view class="changan">
		<view class="item">
			<view class="img">
				<image src="../../static/images/s1.jpeg" mode="widthFix"></image>
			</view>
			<view class="text">
				<view class="title">
					华岳仙掌
				</view>
				<view class="msg">
					西岳华山为国家级风景名胜区，位于西安东120公里的华阴市南。北濒黄河、南依秦岭，奇峰突兀、巍峨壮丽，以“险、奇、峻、绝、幽”而名冠天下。
				</view>
			</view>
		</view>
		<view class="item">
			<view class="img">
				<image src="../../static/images/s2.jpeg" mode="widthFix"></image>
			</view>
			<view class="text">
				<view class="title">
					骊山晚照
				</view>
				<view class="msg">
					骊山位于陕西临潼区城南地区，西距西安市25公里。是秦岭东端的一个支脉，海拔800米，东西长约5公里，南北宽约3公里,最高峰仁宗庙海拔1256米。
				</view>
			</view>
		</view>
		<view class="item">
			<view class="img">
				<image src="../../static/images/s3.jpeg" mode="widthFix"></image>
			</view>
			<view class="text">
				<view class="title">
					灞柳风雪
				</view>
				<view class="msg">
					唐朝时，在灞桥上设立驿站，凡送别亲人与好友东去，多在这里分手，流传着“年年伤别，灞桥风雪”的词句，“灞桥风雪”从此被喻为“关中八景”之一。
				</view>
			</view>
		</view>
		<view class="item">
			<view class="img">
				<image src="../../static/images/s4.jpeg" mode="widthFix"></image>
			</view>
			<view class="text">
				<view class="title">
					曲江流饮
				</view>
				<view class="msg">
					每当新科进士及第、总要在曲江赐宴。新科进士在这里乘兴作乐，放杯至盘上，放盘于曲流上，轻漂漫泛转至谁前。谁就执杯畅饮遂成一时盛事“曲江流饮”由此得名。
				</view>
			</view>
		</view>
		<view class="item">
			<view class="img">
				<image src="../../static/images/s5.jpeg" mode="widthFix"></image>
			</view>
			<view class="text">
				<view class="title">
					雁塔晨钟
				</view>
				<view class="msg">
					小雁塔内有一口金代铸成的大铁钟，据说只要把亲人的名字和去处写在一张黄笺上，钟声就会把思念之情传到千里之外的亲人耳中.因此“雁塔晨钟"被誉为关中八景之一。
				</view>
			</view>
		</view>
		<view class="item">
			<view class="img">
				<image src="../../static/images/s6.jpeg" mode="widthFix"></image>
			</view>
			<view class="text">
				<view class="title">
					咸阳古渡
				</view>
				<view class="msg">
					咸阳古渡”建筑于明嘉靖年间，渡口处建有一座木桥，通陇通蜀，过客众多，为秦中第一渡。“咸阳古渡”为古长安通往西北西南的咽喉要道，处于十分重要的地理位置。
				</view>
			</view>
		</view>
		<view class="item">
			<view class="img">
				<image src="../../static/images/s7.jpeg" mode="widthFix"></image>
			</view>
			<view class="text">
				<view class="title">
					草堂烟雾
				</view>
				<view class="msg">
				草堂寺，相传始建于晋代。传说当年井中央有石一块，每见一蛇卧石上，辄有白雾冲天而上缭绕于帝都长安，因而被称“烟雾井”，形成 “草堂烟雾”。
				</view>
			</view>
		</view>
		<view class="item">
			<view class="img">
				<image src="../../static/images/s8.jpeg" mode="widthFix"></image>
			</view>
			<view class="text">
				<view class="title">
					太白积雪
				</view>
				<view class="msg">
					太白山崇高峻伟，山高云淡、空气稀薄、气候寒冷，终年积雪不化，即使三伏盛暑，皑皑白雪，仍然莽莽天际银光四射，是誉为关中八景之一的“太白积雪”。
				</view>
			</view>
		</view>
	</view>
</template>

<script>
</script>

<style>
	swiper {
		height: 200px;
	}

	.swiper-item image {
		width: 100%;
	}

	.logo {
		text-align: center;
	}

	.changan .item {
		display: flex;
		border: 1rpx solid #ff5500;
		margin: 10rpx;
		padding: 10rpx;
		border-radius: 10rpx;
		box-shadow: 3px 3px 3px #eee
	}

	.changan .item .img {
		width: 220rpx;
		height: 220rpx;
	}

	.changan .item .img image {
		width: 100%;
		height: 100%;
	}

	.changan .item .text {
		width: 480rpx;
	}

	.changan .item .text .title {
		text-align: center;
		font-size: 35rpx;
		font-weight: bold;
		color: #aa0000;
	}

	.changan .item .text .msg {
		color: #666;
		font-size: 28rpx;
		text-indent: 56rpx;
	}
</style>