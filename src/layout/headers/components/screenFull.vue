<template>
  <div @click="handleFullScreen">
    <el-icon v-show="!icon"><FullScreen /></el-icon>
    <el-icon v-show="icon"><Close /></el-icon>
  </div>
</template>

<script setup>
import screenfull from 'screenfull'
import { onBeforeUnmount, onMounted, ref } from 'vue'
const icon = ref(screenfull.isFullscreen)
const handleFullScreen = () => {
  if (screenfull.isEnabled) {
    screenfull.toggle()
  }
}
const changeIcon = () => {
  icon.value = screenfull.isFullscreen
}
onMounted(() => {
  screenfull.on('change', changeIcon)
})
onBeforeUnmount(() => {
  screenfull.off('change')
})
</script>

<style lang="scss" scoped></style>
