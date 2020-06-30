<template>
  <div id="app">
  <Header/>
    <Tasks v-bind:tasks="tasks" v-on:del-task="deleteTask"/>
  </div>
</template>

<script>
import Header from './components/layout/Header';
import Tasks from './components/Tasks';

  export default {
    name: 'app',
    components: {
      Header,
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
            completed: true
          },
          {
            id: 3,
            title: 'Task Three',
            completed: false
          }
        ]
      }
    },
    methods: {
      deleteTask(id) {
        this.tasks = this.tasks.filter(x => x.id != id);
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
