<script setup lang="ts">
import { useCounterStore } from '@/stores/counter'
import AppWrapper from '@/components/AppWrapper/index.vue'

const counterStore = useCounterStore()
</script>

<template>
  <AppWrapper>
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
    </view>
  </AppWrapper>
</template>

<style scoped lang="scss"></style>
