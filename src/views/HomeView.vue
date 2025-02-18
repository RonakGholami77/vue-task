<template>
  <InputComponent v-model:name="name" />
  <DisplayComponent :name="name" :apiResponse="apiResponse" />
</template>

<script setup>
import { ref, watch } from 'vue'
import axios from 'axios'
import { debounce } from 'lodash'
import InputComponent from '@/components/InputComponent.vue'
import DisplayComponent from '@/components/DisplayComponent.vue'

const name = ref('ali')
const apiResponse = ref('')

const fetchData = async (newValue) => {
  if (!newValue.trim()) {
    apiResponse.value = ''
    return
  }
  await axios({
    url: `http://localhost:3000/listName?name_like=${name.value}`,
  }).then((response) => {
    const result = response.data.find((item) => item.name === newValue)
    if (result) {
      apiResponse.value = result
    }
  })
}

const debouncedFetchData = debounce(fetchData, 800)

watch(name, (newValue) => {
  debouncedFetchData(newValue)
})
</script>
