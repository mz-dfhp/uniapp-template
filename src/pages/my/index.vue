<script setup lang="ts">
import { useCounterStore } from '@/stores/counter'
import PageWrapper from '@/components/PageWrapper/index.vue'
import Tabbar from '@/components/Tabbar/index.vue'

const counterStore = useCounterStore()
</script>

<template>
  <PageWrapper>
    <view>
      <view>{{ counterStore.count }}</view>
      <view>
        <button @click="counterStore.decrement()">
          -
        </button>
        <button @click="counterStore.increment()">
          +
        </button>
      </view>
      <Tabbar />
    </view>
  </PageWrapper>
</template>

<style scoped lang="scss"></style>
