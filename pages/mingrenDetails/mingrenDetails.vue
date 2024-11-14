<template>
  <view class="mingren-details">
    <view v-if="loading" class="loading">
      <uni-load-more status="loading"></uni-load-more>
    </view>
    
    <template v-else>
      <view class="title">
        {{mingrenInfo.name}}
      </view>
      <view class="img">
        <image :src="mingrenInfo.pic" mode="aspectFill"></image>
      </view>
      <view class="content">
        {{mingrenInfo.msg}}
      </view>
    </template>
  </view>
</template>

<script setup>
import { onLoad } from '@dcloudio/uni-app'
import { ref } from 'vue'

// 名人数据
const mingrenInfos = ref([{
			name: '霍去病',
			pic: '/static/images/person1.jpg',
			msg: '霍去病（公元前140年—公元前117年）是西汉时期杰出的军事家和民族英雄。他是汉武帝皇后卫子夫及大司马大将军卫青的外甥，同时也是大司马大将军霍光的同父异母兄长。霍去病以勇猛果断和用兵灵活多变著称，善于运用长途奔袭、快速突袭和大迂回、大穿插的战术。'
		},
		{
			name: '陈忠实',
			pic: '/static/images/person2.jpg',
			msg: '陈忠实（1942年8月—2016年4月29日），出生于陕西省西安市灞桥区霸陵乡西蒋村，中国当代作家，陕西省作家协会专业作家、名誉主席，中国作家协会第五、六、七届副主席。'
		},
		{
			name: '班超',
			pic: '/static/images/person3.jpg',
			msg: '班超（32年—102年），字仲升，是东汉时期杰出的军事家和外交家。他出生于扶风平陵（今陕西省咸阳市），是著名史学家班彪的幼子，其长兄班固和妹妹班昭也是著名的史学家。班超为人有大志，内心孝敬恭谨，审察事理，口齿辩给，博览群书。他不甘于为官府抄写文书，投笔从戎，随窦固出击北匈奴，而后率领三十六人出使西域，在汉明帝末年收服了西域部分国家'
		},
		{
			name: '孙思邈',
			pic: '/static/images/person4.jpg',
			msg: '孙思邈（541年—682年），唐代著名的医学家和道士，被后世尊称为"药王"。他出生于京兆华原（今陕西省铜川市耀州区）的一个贫穷农民家庭。孙思邈自幼聪明过人，对道家学说有着浓厚的兴趣，并在陕西终南山中隐居，逐渐获得了很高的声名'
		},
		{
			name: '柳宗元',
			pic: '/static/images/person5.jpg',
			msg: '柳宗元（773年—819年），字子厚，唐代河东（今山西省永济市）人，是唐代著名的文学家、哲学家、散文家和思想家。他因出生于河东，世称"柳河东"、"河东先生"，又因官至柳州刺史，故也称"柳柳州"。柳宗元与韩愈并称"韩柳"，共同倡导唐代古文运动，与刘禹锡并称"刘柳"，与王维、孟浩然、韦应物并称"王孟韦柳"，并与韩愈、欧阳修、苏洵、苏轼、苏辙、王安石、曾巩并称为"唐宋八大家"'
		},
		{
			name: '贾平凹',
			pic: '/static/images/person6.jpg',
			msg: '贾平凹，1952年2月21日生于陕西省商洛市丹凤县棣花镇，当代作家。1974年开始发表作品。1975年毕业于西北大学中文系。1982年发表作品《鬼城》《二月杏》。1992年创刊《美文》。1993年创作《废都》。1997年凭借《满月儿》，获得首届全国优秀短篇小说奖。2003年，先后担任西安建筑科技大学人文学院院长、文学院院长。2008年凭借《秦腔》，获得第七届茅盾文学奖。'
		},
		{
			name: '张艺谋',
			pic: '/static/images/person7.jpg',
			msg: '张艺谋是中国著名的电影导演，1950年4月2日出生于陕西西安，被誉为"第五代导演"的代表人物之一。他的作品在国内外屡获电影奖项，并三次提名奥斯卡和五次提名金球奖。张艺谋的导演生涯起步于1987年，他的第一部电影《红高粱》获得了中国首个国际电影节金熊奖。此后，他执导的《菊豆》、《大红灯笼高高挂》、《秋菊打官司》、《活着》、《一个都不能少》、《我的父亲母亲》等影片在国际上获得了极高的评价和众多奖项'
		},
		{
			name: '闫妮',
			pic: '/static/images/person8.jpg',
			 msg: '闫妮是中国著名的女演员，1971年3月10日出生于陕西省西安市。她毕业于陕西财经学院企业管理专业，之后考入兰州军区战斗歌舞团，再考入解放军艺术学院表演专业，1994年调入空政歌舞团。闫妮在2005年因主演《武林外传》中的佟湘玉一角而一炮走红，被广大观众所熟知。她的演技精湛，凭借《北风那个吹》和《三七撞上二十一》等作品获得了第27届飞天奖和第25届金鹰奖"视后"的荣誉。'
		},
		{
			name: '郭达',
			pic: '/static/images/person9.jpg',
			msg: '郭达，1955年6月9日出生于陕西省西安市，是中国内地男演员、国家一级演员。他毕业于上海戏剧学院，1987年在春晚上搭档杨蕾出演小品《产房门前》。郭达以其在春晚上的表演而广为人知，特别是与蔡明的多次合作，给观众带来了许多欢笑。他的作品不仅限于小品，还包括多部电影和电视剧，如1990年的喜剧电影《现世活宝》，2001年春晚小品《红娘》，以及2004年与郭冬临、杨蕾合作的小品《好人不打折》'
		},
		{
			name: '路遥',
			pic: '/static/images/person10.jpg',
			msg: '路遥（1949年12月3日—1992年11月17日），原名王卫国，是中国当代现实主义作家，出生于陕北榆林清涧县的一个贫困农民家庭。他毕业于延安大学，曾任《陕西文艺》编辑、中国作协陕西分会副主席。路遥的文学创作始于1973年，他的代表作《平凡的世界》于1991年获得了第三届茅盾文学奖。2018年12月18日，中共中央、国务院授予其"改革先锋"人物称号，2019年9月，他又被获授新中国七十年"最美奋斗者"称号。'
		}
	])

const mingrenInfo = ref({})
const loading = ref(true)

onLoad((options) => {
  const index = options.index
  try {
    uni.setNavigationBarTitle({
      title: mingrenInfos.value[index].name
    })
    mingrenInfo.value = mingrenInfos.value[index]
  } catch (error) {
    uni.showToast({
      title: '加载失败',
      icon: 'none'
    })
  } finally {
    loading.value = false
  }
})
</script>

<style>
.mingren-details {
  padding: 20rpx;
}

.title {
  font-size: 40rpx;
  color: #333;
  text-align: center;
  margin: 20rpx 0 40rpx;
  font-weight: bold;
}

.img {
  width: 100%;
  height: 450rpx;
  border-radius: 16rpx;
  overflow: hidden;
  box-shadow: 0 4rpx 12rpx rgba(0,0,0,0.1);
}

.img image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.content {
  margin: 40rpx 20rpx;
  font-size: 32rpx;
  color: #666;
  line-height: 1.8;
  text-indent: 2em;
  letter-spacing: 2rpx;
}

@media screen and (min-width: 768px) {
  .mingren-details {
    max-width: 960px;
    margin: 0 auto;
  }
  
  .img {
    height: 600rpx;
  }
}
</style> 