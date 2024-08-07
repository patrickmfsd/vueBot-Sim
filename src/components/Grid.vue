<!-- Grid.vue -->
<template>
  <div class="grid-container">
    <div
        v-for="(row, rowIndex) in rows"
        :key="'row-' + rowIndex"
        class="grid-row"
    >
      <div
          v-for="(col, colIndex) in columns"
          :key="'col-' + colIndex"
          class="grid-cell"
          :class="{'robot': isRobotPosition(rowIndex, colIndex)}"
      >
        <svg
            v-if="isRobotPosition(rowIndex, colIndex)"
            fill="whitesmoke"
            width="80px"
            height="80px"
            viewBox="0 -64 640 640"
            xmlns="http://www.w3.org/2000/svg"
            :style="{ transform: `rotate(${rotation}deg)` }"
        >
          <path d="M32,224H64V416H32A31.96166,31.96166,0,0,1,0,384V256A31.96166,31.96166,0,0,1,32,224Zm512-48V448a64.06328,64.06328,0,0,1-64,64H160a64.06328,64.06328,0,0,1-64-64V176a79.974,79.974,0,0,1,80-80H288V32a32,32,0,0,1,64,0V96H464A79.974,79.974,0,0,1,544,176ZM264,256a40,40,0,1,0-40,40A39.997,39.997,0,0,0,264,256Zm-8,128H192v32h64Zm96,0H288v32h64ZM456,256a40,40,0,1,0-40,40A39.997,39.997,0,0,0,456,256Zm-8,128H384v32h64ZM640,256V384a31.96166,31.96166,0,0,1-32,32H576V224h32A31.96166,31.96166,0,0,1,640,256Z"/>
        </svg>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed, defineProps } from 'vue';

const props = defineProps({
  rows: {
    type: Number,
    default: 5
  },
  columns: {
    type: Number,
    default: 5
  },
  robotPosition: {
    type: Object,
    default: () => ({ x: 2, y: 2 })
  },
  robotDirection: {
    type: String,
    default: 'N'
  },
  hitWall: {
    type: Boolean,
    default: false
  }
});

const rotation = computed(() => {
  switch (props.robotDirection) {
    case 'N':
      return 0;
    case 'E':
      return 90;
    case 'S':
      return 180;
    case 'W':
      return 270;
    default:
      return 0;
  }
});

const isRobotPosition = (row, col) => {
  return row === props.robotPosition.y && col === props.robotPosition.x;
};
</script>

<style scoped>
  .grid-container {
    display: grid;
    justify-content: center;
    align-items: center;
    margin: 30px auto;
  }

  .grid-row {
    display: flex;
  }

  .grid-cell {
    width: 100px;
    height: 100px;
    background-color: var(--color-background-mute); /* Light gray for a subtle appearance */
    border: 1px solid var(--color-border); /* Slightly darker gray for the border */
  }

  .grid-cell.robot {
    background-color: var(--orange); /* Highlight color for robot */
    text-align: center;
    padding: 10px;
  }
</style>