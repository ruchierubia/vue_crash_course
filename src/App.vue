<template>
  <div id="app">
    <Tasks/>
  </div>
</template>

<script>
import Tasks from './components/Tasks.vue';

  export default {
    name: 'app',
    components: {
      Tasks
    },
    data() {
      return {
        tasks: [
          {
            id: 1,
            title: 'Task One',
            completed: false
          },
          {
            id: 2,
            title: 'Task Two',
            completed: false
          },
          {
            id: 3,
            title: 'Task Three',
            completed: false
          }
        ]
      }
    } 
  }
</script>

<style>
  *{ 
    box-sizing: border-box;
    margin: 0;
    padding: 0;

  }

  body {
    font-family: Arial, Helvetica, sans-serif;;
    line-height: 1.4;
  }
</style>
