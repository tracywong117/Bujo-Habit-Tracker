<template>
  <div id="app">
    <HabitTable />
  </div>
</template>

<script>
import HabitTable from './components/HabitTable.vue';

export default {
  name: 'App',
  components: {
    HabitTable,
  },
};
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  text-align: center;
}

.custom-checkbox {
  position: relative;
  display: inline-block;
  width: 20px;
  height: 20px;
  margin: 10px;
  cursor: pointer;
}

.custom-checkbox input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

.checkmark {
  position: absolute;
  top: 0;
  left: 0;
  height: 20px;
  width: 20px;
  background-color: transparent;
  border-radius: 50%;
}

.checkmark::after {
  content: "";
  position: absolute;
  display: none;
}

.custom-checkbox input:checked+.checkmark::after {
  display: block;
}

.custom-checkbox .checkmark::after {
  left: 4px;
  /* Adjust positioning for the bigger tick */
  top: 2px;
  /* Adjust positioning for the bigger tick */
  width: 10px;
  /* Increase the width for a bigger tick */
  height: 18px;
  /* Increase the height for a bigger tick */
  border: solid rgb(174, 73, 90);
  border-width: 0 3px 3px 0;
  /* Increase the border width for a thicker tick */
  transform: rotate(45deg) scale(0);
  transition: transform 0.4s ease-in-out;
  transition-delay: 0.3s;
  /* Delay to ensure the circle animation completes */
}

.custom-checkbox input:checked+.checkmark::after {
  transform: rotate(45deg) scale(1);
}

.custom-checkbox .circle {
  position: absolute;
  top: -2.5px;
  left: -5px;
  width: 30px;
  height: 30px;
  border: 2px dotted pink;
  border-radius: 50%;
  opacity: 0;
  animation: circleAnimation 0.6s ease-in-out;
}

@keyframes circleAnimation {
  0% {
    opacity: 0;
    transform: scale(0.5);
  }

  50% {
    opacity: 1;
    transform: scale(1);
  }

  100% {
    opacity: 0;
    transform: scale(1.5);
  }
}

.custom-checkbox input:not(:checked)+.checkmark+.circle {
  display: none;
}
</style>
