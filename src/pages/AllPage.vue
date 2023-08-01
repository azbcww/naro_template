<script setup lang="ts">
import { count } from 'console'
import { type } from 'os'
import { ref, onMounted } from 'vue'
const allInfo = ref()
onMounted(async () => {
  const res = await fetch('/api/all')
  if (res.ok) {
    allInfo.value = await res.json()
  }
})
</script>

<template>
  <div>
    <h1>All</h1>
    <!-- <div v-if="allInfo">{{ allInfo[0].name.String }}</div>
    <div v-else>国一覧が見つかりませんでした</div> -->
    <ul>
      <li v-for="item in allInfo" :key="item">
        <a v-bind:href="'country/'+item.code.String">{{ item.name.String }}</a>
      </li>
    </ul>
  </div>
</template>
