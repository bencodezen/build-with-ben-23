<script setup>
import { useColorMode } from '@vueuse/core'
import HelloWorld from './components/HelloWorld.vue'
import IconMoon from './components/IconMoon.vue'
import IconSun from './components/IconSun.vue'

const colorMode = useColorMode()

const switchTheme = () => {
  colorMode.value = colorMode.value === 'dark' ? 'light' : 'dark'
}
</script>

<template>
  <header
    style="
      display: flex;
      justify-content: space-between;
      height: 50px;
      align-items: center;
    "
  >
    <h1 style="font-size: 1.2rem">Build with Ben #23</h1>
    <button @click="switchTheme" style="display: flex; align-items: center">
      <IconSun v-if="colorMode === 'light'" />
      <IconMoon v-else-if="colorMode === 'dark'" />
    </button>
  </header>
  <h1>{{ colorMode }}</h1>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Hello Vue 3 + Vite" />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.dark {
  background-color: #222;
  color: #fff;
}
</style>
