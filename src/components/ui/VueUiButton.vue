<template>
  <button class="reset-button custom-button">{{ props.text }}</button>
</template>

<script setup>
const props = defineProps({
  text: {
    type: String,
    required: true
  },
})
</script>

<style scoped>
.reset-button {
  border-width: 0;
  padding: 0;
}

.custom-button {
  height: 100%;
  border-radius: 5px;
  font-size: 16px;
  padding: 5px;
  background: #d9d9d9;
  color: white;
  cursor: pointer;
}
</style>