<!-- About.vue -->
<template>
  <div class="about-container">
    <p><strong>Help the robot navigate the grid by using the controls.</strong></p>
    <p>Built as part of a Front End Developer Job Application. </p>
    <p>Built using <a href="https://vuejs.org">vue.js</a> using <a href="https://www.jetbrains.com/webstorm/">JetBrains WebStorm IDE</a>.</p>
  </div>
</template>

<style scoped>
  .about-container {
    text-align: center;
    font-weight: bold;
    color: whitesmoke;
    padding: 2em;
    background: var(--green);;
  }
  strong {
    font-weight: bold;
    font-size: 22px;
  }
  p {
    font-size: 16px;
    font-weight: 500;
  }

  a {
    text-decoration: none;
  }
  a:hover, a:visited {
    color: var(--orange);
  }
</style>
<script setup lang="ts">
</script>