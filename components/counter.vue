<template >
    <div>
      <h1>Counter</h1>
      <p>{{ count }}</p>
      <button @click="count++">Increment</button>
    </div>
  </template> 
<script setup>
    import { ref } from 'vue'
    const count =  ref(0) //init the count to 0 (parameter 0)
</script>