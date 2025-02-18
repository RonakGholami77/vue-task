<script setup>
defineProps({
  name: {
    type: String,
    required: true,
  },
  apiResponse: {
    type: String,
    required: true,
  },
})
</script>

<template>
  <h3>Display Component</h3>
  <p>Name: {{ name }}</p>
  <p>Api Response: {{ apiResponse }}</p>
</template>
