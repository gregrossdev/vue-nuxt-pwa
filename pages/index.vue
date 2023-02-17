<script lang="ts" setup>

const date = new Date(); 
const yearDefault = "2023"
const month = ("0" + (date.getMonth() + 1))
const day = date.getDate()
const today = `${yearDefault}-${month}-${day}`

const { data: jft, pending } = await useLazyFetch(`https://jimmy-smith.gregross.host/api/dates/${today}`, {
    transform: (jft) => jft.data,
})


</script>



<template>
  <div v-if = pending>
    pending.... 
  </div>
  <div v-else>
    <h2>{{jft.date}}</h2>
    <h2>{{jft.title}}</h2>
    <section v-html = jft.content />
  </div>
</template>

<style scoped></style>
