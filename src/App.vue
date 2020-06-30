<template>
  <div id="app">
    <Header/>
    <AddTask/>
    <Tasks v-bind:tasks="tasks" v-on:del-task="deleteTask"/>
  </div>
</template>

<script>
import Header from './components/layout/Header';
import Tasks from './components/Tasks';
import AddTask from './components/AddTask';

  export default {
    name: 'app',
    components: {
      Header,
      Tasks,
      AddTask
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

  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background: #777;
  }
</style>
