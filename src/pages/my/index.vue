<script setup lang="ts">
import { useCounterStore } from '@/stores/counter'

const counterStore = useCounterStore()
</script>

<template>
  <view class="content">
    <view>{{ counterStore.count }}</view>
    <view>
      <button @click="counterStore.decrement()">
        -
      </button>
      <button @click="counterStore.increment()">
        +
      </button>
    </view>
  </view>
</template>

<style scoped lang="scss"></style>
