<script setup lang="ts">
import { ref, onMounted } from 'vue'
const props = defineProps<{ countryName: string }>()
const countryInfo = ref()
onMounted(async () => {
  const res = await fetch('/api/country/' + props.countryName)
  if (res.ok) {
    countryInfo.value = await res.json()
  }
})
</script>

<template>
  <div>
    <h1>
      {{ countryName }}
    </h1>
    <!-- <div v-if="countryInfo">{{ countryInfo }}</div>
    <div v-else>国が見つかりませんでした</div> -->
    <ul>
      <li v-for="item in countryInfo" :key="item">
        <a v-bind:href="'/city/' + item.name.String">{{ item.name.String }}</a>
      </li>
    </ul>
  </div>
</template>
