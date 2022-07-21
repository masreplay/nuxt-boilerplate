<script lang="ts" setup>
const a = useMain()

const x = ref(1)

function increase() {
  x.value++;
}

const layout = "custom";
</script>

<template>
  <NuxtLayout :name="layout">

    Page: foo {{ x }}
    <NuxtLink to="/users-admins/123">Home page</NuxtLink>
    <v-btn depressed elevation="11" icon outlined plain raised @click="increase"></v-btn>

  </NuxtLayout>

</template>

<style scoped>
.hello {
  color: red;
}
</style>
