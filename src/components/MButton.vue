<script setup>
const props = defineProps({
  text: String
})
</script>

<template>
  <button>{{ props.text }}</button>
</template>

<style scoped>
button {
  background-color: blue;
  color: #fff;
  border: none;
  border-radius: 5px;
  padding: 10px;
  font-size: 1.2rem;
  cursor: pointer;
  margin: 5px;
}

button:hover {
  background-color: darkblue;
}
</style>
