<script lang="ts" setup>
const config = useRuntimeConfig()

const foo = useFoo()

type Paging<T> = {
  results: Array<T>
  count: number
};

const skip = ref(0)
const { pending, data, refresh, error } = await useFetch<Paging<any>>(() => `realestate?skip=${skip.value}&take=10`, { baseURL: config.public.apiBase });
function nuxt() {
  skip.value += 10;
  refresh()
}
function previous() {
  skip.value -= 10;
  refresh()
}

function navigateToUser(id: string) {
  return navigateTo({
    path: `/real-estate/${id}`,
  })
}
</script>
<template>
  <div v-if="pending"> Loading... </div>
  <div v-else-if="error"> error {{ error }}</div>
  <div v-else>
    {{foo}}
    <v-btn color="success" @click="nuxt" v-if="skip <= data.count">nuxt</v-btn>
    <h1>{{ skip / 10 + 1 }}</h1>
    <v-btn color="error" @click="previous" v-if="skip >= 10">previous</v-btn>
    <div v-for="realEstate in data.results" @click="navigateToUser(realEstate.id)">
      {{ realEstate.title }}
      {{ realEstate.id }}
    </div>
  </div>
</template>
<style scoped>
</style>