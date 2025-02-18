<script setup>
defineProps({
  name: {
    type: String,
    required: true,
  },
})

const emit = defineEmits(['update:name'])

const changeValue = (event) => {
  emit('update:name', event.target.value)
}
</script>

<template>
  <label for="name">Name:</label>
  <input id="name" autocomplete="off" type="text" :value="name" @input="changeValue" />

  <hr />
</template>
