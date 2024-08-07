<!-- HeaderComponent.vue -->
<template>
  <header class="header">
    <h1>{{ title }}</h1>
  </header>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: 'My Application'
    }
  }
}
</script>

<style scoped>
  .header {
    background-color: #333;
    color: white;
    padding: 10px 20px;
    text-align: center;
  }

  .header h1 {
    margin: 0;
  }
</style>