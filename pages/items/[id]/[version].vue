<script lang="ts" setup>
const route = useRoute()

const version: number = route.params.version as any

const id: number = route.params.id as any
</script>

<template>
  <div>
    <div v-if="version == 1"> hello {{ id }} </div>
    <div v-if="version == 2"> hello new design {{ id }} </div>
  </div>
</template>

<style scoped>
</style>
