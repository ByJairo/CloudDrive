<template>
  <input class="form-control" type="text" placeholder="搜索文件" aria-label="Search" v-model="q"
         @keydown.enter.prevent="handleEnterKey"/>
</template>
<script setup>
import {ref} from 'vue'

const q = ref("hello world")
const emits = defineEmits(["handleValueQ"])

const handleEnterKey = () => {
  emits("handleValueQ", q.value)
}
</script>
<style scoped>

</style>
