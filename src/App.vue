<script setup>
import { ref } from 'vue';
import Header from './components/Header.vue';
import Grid from './components/Grid.vue';
import Controller from './components/Controller.vue';
import About from "./components/About.vue";

// Grids and Rows
const rows = 5;
const columns = 5;

// State management for robot's position, robot starts in middle
const robotPosition = ref({ x: 2, y: 2 });
// State management for robot's direction, robot starts in middle
const robotDirection = ref('N');
// Track if robot hits a wall
const hitWall = ref(false);

// Methods to control the robot
const moveForward = () => {
  hitWall.value = false; // Reset hitWall state
  switch (robotDirection.value) {
    case 'N':
      if (robotPosition.value.y > 0) robotPosition.value.y -= 1;
      else hitWall.value = true; // Robot hits the wall
      break;
    case 'E':
      if (robotPosition.value.x < columns - 1) robotPosition.value.x += 1;
      else hitWall.value = true; // Robot hits the wall
      break;
    case 'S':
      if (robotPosition.value.y < rows - 1) robotPosition.value.y += 1;
      else hitWall.value = true; // Robot hits the wall
      break;
    case 'W':
      if (robotPosition.value.x > 0) robotPosition.value.x -= 1;
      else hitWall.value = true; // Robot hits the wall
      break;
  }
};

const turnLeft = () => {
  const directions = ['N', 'W', 'S', 'E'];
  const currentIndex = directions.indexOf(robotDirection.value);
  robotDirection.value = directions[(currentIndex + 1) % directions.length];
};

const turnRight = () => {
  const directions = ['N', 'E', 'S', 'W'];
  const currentIndex = directions.indexOf(robotDirection.value);
  robotDirection.value = directions[(currentIndex + 1) % directions.length];
};
</script>

<template>
  <main>
    <Header title="Robot Grid" />
    <About />
    <Grid
        :rows="rows"
        :columns="columns"
        :robotPosition="robotPosition"
        :robotDirection="robotDirection"
        :hitWall="hitWall"
    />
    <Controller
        @moveForward="moveForward"
        @turnLeft="turnLeft"
        @turnRight="turnRight"
    />
  </main>
</template>

<style scoped>


</style>
