<script lang="ts" setup>
import { useRoute } from 'vue-router';

const config = useRuntimeConfig()
const route = useRoute()
const { pending, data, refresh, error } = await useFetch<any>(() => `realestate/${route.params.id}`, { baseURL: config.public.apiBase });
</script>

<template>
  <div>
    {{ data.title }}
  </div>
</template>

<style scoped>
</style>
