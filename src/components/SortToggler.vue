<script setup>
import {reactive} from 'vue'

const toggle = () => {
  sort.order = sort.order === "asc" ? "desc" : "asc"
}
const sort = reactive({
  column: "name",
  order: "asc"
})
</script>
<template>
  <button @click="toggle" class="rounded-button">

    <icon-arrow-up v-if="sort.order==='asc'"/>
    <icon-arrow-down v-else/>
  </button>
</template>

<style scoped>

</style>
