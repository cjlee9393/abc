<script setup>
defineProps(['modelValue'])
defineEmits(['update:modelValue'])
</script>

<template>
  <main>
      <input type="radio" name="auth" id="Customer" value="Customer" @click="$emit('update:modelValue', $event.target.value)" checked />
      <label for="Customer">Customer</label> 

      <input type="radio" name="auth" id="Admin" value="Admin" @click="$emit('update:modelValue', $event.target.value)" />
      <label for="Admin">Admin</label>
  </main>
</template>

<style scoped>

</style>