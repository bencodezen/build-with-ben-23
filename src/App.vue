<script setup>
import { ref } from 'vue'
import { useColorMode, useDraggable } from '@vueuse/core'
import IconCafe from './components/IconCafe.vue'
import IconMoon from './components/IconMoon.vue'
import IconSun from './components/IconSun.vue'

const colorMode = useColorMode({
  modes: {
    cafe: 'cafe'
  }
})

const elNotImportantTitle = ref(null)
const elImportantTitle = ref(null)
const elNotUrgentTitle = ref(null)
const elUrgentTitle = ref(null)

const { style } = useDraggable(elNotImportantTitle, {
  initialValue: { x: 40, y: 40 }
})

const { style: style2 } = useDraggable(elImportantTitle, {
  initialValue: { x: 60, y: 60 }
})

const { style: style3 } = useDraggable(elNotUrgentTitle, {
  initialValue: { x: 80, y: 80 }
})

const { style: style4 } = useDraggable(elUrgentTitle, {
  initialValue: { x: 100, y: 100 }
})

const switchTheme = () => {
  if (colorMode.value === 'dark') {
    colorMode.value = 'cafe'
  } else if (colorMode.value === 'cafe') {
    colorMode.value = 'light'
  } else {
    colorMode.value = 'dark'
  }
}
</script>

<template>
  <header
    style="
      display: flex;
      justify-content: space-between;
      height: 50px;
      align-items: center;
      border-bottom: 1px solid #ccc;
      padding-bottom: 10px;
    "
  >
    <h1 style="font-size: 1.2rem">Build with Ben #23</h1>
    <button @click="switchTheme" style="display: flex; align-items: center">
      <IconSun v-if="colorMode === 'light'" />
      <IconMoon v-else-if="colorMode === 'dark'" />
      <IconCafe v-else />
    </button>
  </header>
  <main>
    <h2>Whiteboard Canvas</h2>
    <div class="whiteboard">
      <div class="whiteboard-section">
        <h3 ref="elNotImportantTitle" :style="style" style="position: fixed">
          Not Important
        </h3>
      </div>
      <div class="whiteboard-section">
        <h3 ref="elImportantTitle" :style="style2" style="position: fixed">
          Important
        </h3>
      </div>
      <div class="whiteboard-section">
        <h3 ref="elNotUrgentTitle" :style="style3" style="position: fixed">
          Not Urgent
        </h3>
      </div>
      <div class="whiteboard-section">
        <h3 ref="elUrgentTitle" :style="style4" style="position: fixed">
          Urgent
        </h3>
      </div>
    </div>
  </main>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.cafe {
  filter: sepia(0.9) hue-rotate(315deg) brightness(0.9);
}

.dark {
  background-color: #222;
  color: #fff;
}

.whiteboard {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 1fr 1fr;
}

.whiteboard-section {
  border: 1px solid #ccc;
  min-height: 200px;
}
</style>
