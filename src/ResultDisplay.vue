<template>
  <div v-if="error" class="alert alert-danger mt-3">{{ error }}</div>
  <div v-else-if="result !== null" class="alert alert-success mt-3">Result: {{ result }}</div>
</template>

<script setup>
const props = defineProps({
  result: Number,
  error: String
})
</script>
