<template>
  <div class="container py-3">
    <ActionsBar/>
    <div class="d-flex justify-content-between align-items-center py-2">
      <h6 class="text-muted mb-0">文件</h6>
      <SortToggler @sort-change="handleSortChange($event)"/>
    </div>
    <FilesList :files="files"/>
  </div>

</template>

<script setup>
import ActionsBar from '../components/ActionsBar.vue'
import axios from 'axios'
import {ref, onMounted, reactive, watchEffect} from 'vue'
import FilesList from '../components/files/FilesList.vue'
import SortToggler from '../components/SortToggler.vue'

const props = defineProps({
  q: {
    type: String
  }
})

const files = ref([])

const query = reactive({
  _sort: "name",
  _order: "asc",
  q: ""
})

watchEffect(async () => {
  query.q = props.q
  const {data} = await axios.get(`http://localhost:3031/files?${new URLSearchParams(query)}`)
  files.value = data
})
const handleSortChange = (payload) => {
  // console.log(payload)
  query._sort = payload.column
  query._order = payload.order
}


</script>

<style scoped>

</style>
