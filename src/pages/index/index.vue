<script setup lang="ts">
import { ref } from 'vue'
import PageWrapper from '@/components/PageWrapper/index.vue'
import Tabbar from '@/components/Tabbar/index.vue'

const title = ref('index')
</script>

<template>
  <PageWrapper>
    <view>
      {{ title }}
      <Tabbar />
    </view>
  </PageWrapper>
</template>

<style scoped lang="scss"></style>
