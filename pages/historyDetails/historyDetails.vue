<template>
  <view class="history-details">
    <view v-if="loading" class="loading">
      <uni-load-more status="loading"></uni-load-more>
    </view>
    
    <template v-else>
      <view class="title">
        {{historyInfo.name}}
      </view>
      <view class="img">
        <image :src="historyInfo.pic" mode="aspectFill"></image>
      </view>
      <view class="content">
        {{historyInfo.msg}}
      </view>
    </template>
  </view>
</template>

<script setup>
import { onLoad } from '@dcloudio/uni-app'
import { ref } from 'vue'

// 历史古迹数据
const historyInfos = ref([
  {
    name: '秦兵马俑',
    pic: '/static/images/h1.jpg',
    msg: '兵马俑，即秦始皇陵兵马俑，是世界八大奇迹之一。1974年被发现，1987年被联合国教科文组织列入《世界遗产名录》。兵马俑规模宏大，气势磅礴，被誉为"世界第八大奇迹"。兵马俑展现了秦始皇时期的军队装备、军事组织、军事科技和军事艺术，是研究秦代军事、政治、经济、文化、艺术和科技发展的重要实物资料。'
  },
  {
    name: '大雁塔',
    pic: '/static/images/h2.jpg',
    msg: '大雁塔位于唐长安城晋昌坊（今陕西省西安市南郊），是中国佛教标志性建筑之一。始建于唐永徽三年（652年），是为了保存玄奘法师从印度取经带回的经典而建造的。塔高64.5米，共七层，是一座楼阁式砖塔。大雁塔不仅是一座重要的佛教建筑，更是古都西安的象征。'
  },
  {
    name: '明城墙',
    pic: '/static/images/h3.jpg',
    msg: '西安钟楼始建于明洪武十七年（1384年），位于西安市中心。钟楼高36米，建筑面积1377平方米。鼓楼始建于明洪武十七年（1384年），现存建筑为清乾隆重建。钟鼓楼是古都长安的标志性建筑，见证了西安千年古都的沧桑变迁。'
  },
  {
    name: '华清池',
    pic: '/static/images/h4.jpg',
    msg: '西安城墙始建于隋朝，现存城墙建于明朝洪武年间，是中国现存规模最大、保存最完整的古代城垣。城墙全长13.74公里，高12米，顶宽12-14米，底宽15-18米。城墙上建有护城河、吊桥、闸楼、箭楼、角楼等古代军事设施，是研究中国古代城市防御体系的重要实物资料。'
  },
  {
    name: '明钟楼',
    pic: '/static/images/h5.jpg',
    msg: '华清池位于西安临潼区，始建于周朝，因唐玄宗与杨贵妃的爱情故事而闻名于世。园内有九大景区，包括温泉遗址、唐代建筑群、仿古建筑群等。华清池不仅是一处重要的历史文化遗址，也是了解唐代建筑艺术和皇家园林的重要场所。'
  },
  {
    name: '历史博物馆',
    pic: '/static/images/h6.jpg',
    msg: '华清池位于西安临潼区，始建于周朝，因唐玄宗与杨贵妃的爱情故事而闻名于世。园内有九大景区，包括温泉遗址、唐代建筑群、仿古建筑群等。华清池不仅是一处重要的历史文化遗址，也是了解唐代建筑艺术和皇家园林的重要场所。'
  },
  {
    name: '大唐芙蓉园',
    pic: '/static/images/h7.jpg',
    msg: '华清池位于西安临潼区，始建于周朝，因唐玄宗与杨贵妃的爱情故事而闻名于世。园内有九大景区，包括温泉遗址、唐代建筑群、仿古建筑群等。华清池不仅是一处重要的历史文化遗址，也是了解唐代建筑艺术和皇家园林的重要场所。'
  },
  {
    name: '大唐不夜城',
    pic: '/static/images/h8.jpg',
    msg: '华清池位于西安临潼区，始建于周朝，因唐玄宗与杨贵妃的爱情故事而闻名于世。园内有九大景区，包括温泉遗址、唐代建筑群、仿古建筑群等。华清池不仅是一处重要的历史文化遗址，也是了解唐代建筑艺术和皇家园林的重要场所。'
  },
  {
    name: '回民巷',
    pic: '/static/images/h9.jpg',
    msg: '华清池位于西安临潼区，始建于周朝，因唐玄宗与杨贵妃的爱情故事而闻名于世。园内有九大景区，包括温泉遗址、唐代建筑群、仿古建筑群等。华清池不仅是一处重要的历史文化遗址，也是了解唐代建筑艺术和皇家园林的重要场所。'
  },
  {
    name: '永兴坊',
    pic: '/static/images/h10.jpg',
    msg: '华清池位于西安临潼区，始建于周朝，因唐玄宗与杨贵妃的爱情故事而闻名于世。园内有九大景区，包括温泉遗址、唐代建筑群、仿古建筑群等。华清池不仅是一处重要的历史文化遗址，也是了解唐代建筑艺术和皇家园林的重要场所。'
  }
])

const historyInfo = ref({})

const loading = ref(true)

onLoad((options) => {
  const index = options.index
  try {
    uni.setNavigationBarTitle({
      title: historyInfos.value[index].name
    })
    historyInfo.value = historyInfos.value[index]
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
.history-details {
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

/* 添加响应式支持 */
@media screen and (min-width: 768px) {
  .history-details {
    max-width: 960px;
    margin: 0 auto;
  }
  
  .img {
    height: 600rpx;
  }
}
</style>
