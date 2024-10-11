<template>
    <div>{{ twoot }}</div>
  </template>
  
  <script>
  
  
  export default {
    name: 'TwootItem',
    props: {
        twoot: {
            type: String,
            required: true
        }
    }
  }

  </script>
  
  <style>

  </style>
  