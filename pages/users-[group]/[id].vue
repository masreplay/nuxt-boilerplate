<script lang="ts" setup>
const route = useRoute()

if (route.params.group === 'admins' && !route.params.id) {
  console.log('Warning! Make sure user is authenticated!')
}
</script>

<template>
  <div>
    {{ $route.params.group }} - {{ $route.params.id }}
  </div>
</template>

<style scoped>
</style>
