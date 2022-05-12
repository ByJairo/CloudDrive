<template>
  <nav class="navbar navbar-light bg-white navbar-expand-lg border-bottom">
    <div class="container">
      <a class="navbar-brand" href="/">
        <strong>Vue3.2</strong>
        CouldDrive @Jairo
      </a>
      <form class="form-inline mt-2 mt-md-0">
        <SearchForm @handleValueQ="sendQToApp($event)"/>
      </form>
    </div>
  </nav>
</template>
<script setup>
import SearchForm from '../components/SearchForm.vue'

const emits = defineEmits(["handleValueQ"])

const sendQToApp = (value) => {
  // console.log(value)
  emits("handleValueQ", value)
}

</script>
<style scoped>

</style>
