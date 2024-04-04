<script setup lang="ts">
import { getCurrentInstance, onMounted, ref } from 'vue'
import SafeArea from '@/components/SafeArea/index.vue'

//
import Index from '@/assets/svg/index.svg'
import IndexActive from '@/assets/svg/index-active.svg'
import Classify from '@/assets/svg/classify.svg'
import ClassifyActive from '@/assets/svg/classify-active.svg'
import My from '@/assets/svg/my.svg'
import MyActive from '@/assets/svg/my-active.svg'

const tabbarHeight = ref(0)
const activePath = ref('')

const list = [
  {
    title: '首页',
    path: '/pages/index/index',
    icon: Index,
    iconActive: IndexActive,
  },
  {
    title: '分类',
    path: '/pages/classify/index',
    icon: Classify,
    iconActive: ClassifyActive,
  },
  {
    title: '我的',
    path: '/pages/my/index',
    icon: My,
    iconActive: MyActive,
  },
]

function onChange(item: typeof list[number]) {
  uni.switchTab({
    url: item.path,
  })
}

function setActivePathPath() {
  const pages = getCurrentPages()
  const page = pages[pages.length - 1]
  activePath.value = `/${page.route}`
}

function setTabbarHeight() {
  const query = uni.createSelectorQuery().in(getCurrentInstance())
  query.select('.tabbar-wrapper').boundingClientRect()
  query.exec((res) => {
    const rect = res[0]
    tabbarHeight.value = rect.height
  })
}

onMounted(() => {
  // #ifdef H5
  uni.hideTabBar()
  // #endif
  setActivePathPath()
  setTabbarHeight()
})
</script>

<template>
  <view>
    <view class="tabbar-wrapper">
      <view class="tabbar-list">
        <view
          v-for="(item) in list" :key="item.path"
          class="tabbar-list-item"
          :class="activePath === item.path ? 'tabbar-list-item-active' : ''"
          @click="onChange(item)"
        >
          <image
            :src="activePath === item.path ? item.iconActive : item.icon"
            class="list-item-icon"
          />
          <view class="list-item-title">
            {{ item.title }}
          </view>
        </view>
      </view>
      <SafeArea />
    </view>
    <view :style="{ height: `${tabbarHeight}px`, opacity: 0 }" />
  </view>
</template>

<style scoped lang="scss">
.tabbar-wrapper {
  position: fixed;
  width: 100vw;
  bottom: 0;
  left: 0;

  .tabbar-list {
    padding: 5rpx 0;
    display: flex;

    .tabbar-list-item {
      flex: 1;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;

      .list-item-title {
        font-size: 22rpx;
        color: #1D1D1D;
      }

      .list-item-icon {
        margin-top: 2rpx;
        width: 44rpx;
        height: 44rpx;
      }
      &.tabbar-list-item-active{
        .list-item-title{
          color: #1578ff;
        }
        .list-item-icon{
          color: #1578ff;
        }
      }
    }
  }
}
</style>
