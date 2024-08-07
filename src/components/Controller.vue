<!-- Controller.vue -->
<template>
  <div class="controller-container">
    <div class="turn-controls">
      <button @click="handleTurnLeft" class="controller-button left-button">Turn Left</button>
      <button @click="handleMoveForward" class="controller-button forward-button" title="Move Forward">
        <svg fill="whitesmoke" height="50px" width="60px"  id="Layer_1" xmlns="http://www.w3.org/2000/svg"
             viewBox="0 0 511.996 511.996" xml:space="preserve">
          <g>
            <g>
              <g>
                <path d="M389.826,121.758l-128-119.467c-3.285-3.055-8.363-3.055-11.648,0l-128,119.467c-1.724,1.613-2.714,3.874-2.714,6.238
                  v136.533c0,3.448,2.082,6.562,5.274,7.885c3.191,1.323,6.852,0.589,9.293-1.852l121.967-121.967l121.967,121.967
                  c1.638,1.63,3.823,2.5,6.033,2.5c1.101,0,2.21-0.213,3.268-0.648c3.192-1.323,5.265-4.437,5.265-7.885V127.996
                  C392.531,125.632,391.55,123.371,389.826,121.758z"/>
                <path d="M261.826,241.225c-3.285-3.055-8.363-3.055-11.648,0l-128,119.467c-1.724,1.613-2.714,3.874-2.714,6.238v136.533
                  c0,3.447,2.082,6.562,5.274,7.885c3.191,1.314,6.852,0.597,9.293-1.852l121.967-121.967l121.967,121.967
                  c1.638,1.63,3.823,2.5,6.033,2.5c1.101,0,2.21-0.213,3.268-0.648c3.192-1.323,5.265-4.437,5.265-7.885V366.929
                  c0-2.364-0.981-4.625-2.705-6.238L261.826,241.225z"/>
              </g>
            </g>
          </g>
        </svg>
      </button>
      <button @click="handleTurnRight" class="controller-button right-button">Turn Right</button>
    </div>
  </div>
</template>

<script setup>
import { defineEmits } from 'vue';

const emit = defineEmits(['moveForward', 'turnLeft', 'turnRight']);

const handleMoveForward = () => {
  emit('moveForward');
};

const handleTurnLeft = () => {
  emit('turnLeft');
};

const handleTurnRight = () => {
  emit('turnRight');
};
</script>

<style scoped>
  .controller-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 10px;
    margin: 20px;
  }

  .controller-button {
    color: white;
    border: none;
    border-radius: 5px;
    font-size: 16px;
    cursor: pointer;
    text-align: center;
    transition: box-shadow 0.3s ease-in-out;
    /* Add shadow for depth */
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  }

  .forward-button {
    background-color: var(--orange);;
    width: 100px;
    height: 100px;
    border-radius: 50px;
    border: 5px solid var(--color-border);
    text-align: center;
    font-weight: bold;
  }

  .left-button, .right-button {
    background-color: var(--color-background-darker);
    width: 100px;
    height: 50px;
    border-radius: 30px;
  }
  .left-button:hover, .right-button:hover {
    background-color: var(--green);
  }

  .forward-button:hover {
    background-color: var(--orange-lighter);
  }

  .controller-button:hover {
    box-shadow: 0 6px 12px rgba(0, 0, 0, 0.3);
  }

  .turn-controls {
    display: flex;
    gap: 10px;
    align-items: center;
  }
</style>