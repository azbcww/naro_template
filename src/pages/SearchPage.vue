<script setup lang="ts">
import { ref } from 'vue'

const cityname = ref<string>('')
const cityInfo = ref()
const search = async () => {
  const res = await fetch('/api/cities/' + cityname.value)
  if (res.ok) {
    cityInfo.value = await res.json()
  }
}
</script>

<template>
  <div class="search">
    <h1>This is an search page</h1>
    <div>
      <input type="text" v-model="cityname" />
    </div>
    <div>
      <button @click="search">search</button>
    </div>
  </div>
  <h1>
    {{ cityname }}
  </h1>
  <div v-if="cityInfo">{{ cityInfo }}</div>
  <div v-else>街が見つかりませんでした</div>
</template>
