<script setup lang="ts">
const props = withDefaults(defineProps<{ position?: 'top' | 'bottom' }>(), {
  position: 'bottom',
})
</script>

<template>
  <view class="safe-area" :class="[`safe-area-${props.position}`]" />
</template>

<style scoped lang="scss">
.safe-area {
    display: block;
    width: 100%;

    &.safe-area-top {
        padding-top: constant(safe-area-inset-top);
        padding-top: env(safe-area-inset-top);
    }

    &.safe-area-bottom {
        padding-bottom: constant(safe-area-inset-bottom);
        padding-bottom: env(safe-area-inset-bottom);
    }
}
</style>
