<script setup lang="ts">
import { useCounterStore } from '@renderer/store/counter'
const counter = useCounterStore()
const ipcHandle = (): void => {
  window.electron.ipcRenderer.send('ping')
  counter.increment()
}
</script>

<template>
  <div class="flex flex-col items-center justify-center gap-4">
    <button @click="ipcHandle">Ping</button>
    <div>Current Count: {{ counter.count }}</div>
  </div>
</template>
