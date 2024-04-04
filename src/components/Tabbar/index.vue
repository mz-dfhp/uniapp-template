<script setup lang="ts">
import { ref } from 'vue'
import SafeArea from '@/components/SafeArea/index.vue'

const tabbarHeight = ref(0)

const list = [
  {
    title: '首页',
    path: '/pages/index/index',
    icon: '',
    iconActive: '',
  },
  {
    title: '分类',
    path: '/pages/classify/index',
    icon: '',
    iconActive: '',
  },
  {
    title: '我的',
    path: '/pages/my/index',
    icon: '',
    iconActive: '',
  },
]

function onChange(item: typeof list[number]) {
  uni.switchTab({
    url: item.path,
  })
}
</script>

<template>
  <view>
    <view class="tabbar-wrapper">
      <view class="tabbar-list">
        <view v-for="(item) in list" :key="item.path" class="tabbar-list-item" @click="onChange(item)">
          <view class="list-item-title">
            {{ item.title }}
          </view>
          <view class="list-item-icon" />
        </view>
      </view>
      <SafeArea />
    </view>
    <view :style="{ height: tabbarHeight, opacity: 0 }" />
  </view>
</template>

<style scoped lang="scss">
.tabbar-wrapper {
  position: fixed;
  width: 100vw;
  bottom: 0;
  left: 0;

  .tabbar-list {
    display: flex;

    .tabbar-list-item {
      flex: 1;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;

      .list-item-title {
        color: darkmagenta;
      }

      .list-item-icon {
        margin-top: 2px;
        width: 25px;
        height: 25px;
        background: #ccc;
      }
    }
  }
}
</style>
