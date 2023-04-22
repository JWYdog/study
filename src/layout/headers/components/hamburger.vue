<template>
  <div class="hamburger-container" @click="toggleClick">
    <el-icon v-show="store.getters.siderType"><Fold /></el-icon>
    <el-icon v-show="!store.getters.siderType"><Expand /></el-icon>
  </div>
</template>

<script setup>
import { useStore } from 'vuex'
const store = useStore()
const toggleClick = () => {
  store.commit('app/changeSiderType')
}
</script>

<style lang="scss" scoped>
.hamburger-container {
  margin-right: 16px;
  box-sizing: border-box;
  cursor: pointer;
}
</style>
