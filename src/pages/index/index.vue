<script setup lang="ts">
import { ref } from 'vue'
import AppWrapper from '@/components/AppWrapper/index.vue'

const title = ref('index')
</script>

<template>
  <AppWrapper>
    <view>
      {{ title }}
    </view>
  </AppWrapper>
</template>

<style scoped lang="scss"></style>
