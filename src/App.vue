<template>
  <div id="app">
    <Header/>
    <AddTask v-on:add-task="addTask"/>
    <Tasks v-bind:tasks="tasks" v-on:del-task="deleteTask"/>
  </div>
</template>

<script>
import Header from './components/layout/Header';
import Tasks from './components/Tasks';
import AddTask from './components/AddTask';
import axios from 'axios';

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
        ]
      }
    },
    methods: {
      deleteTask(id) {
        this.tasks = this.tasks.filter(x => x.id != id);
      },
      addTask(newTask) {
        this.tasks = [...this.tasks, newTask];
      }
    },
    // 
    created() {
      axios.get('https://jsonplaceholder.typicode.com/todos')
      .then(res => this.tasks = res.data)
      .catch(err =>  console.log(err));
      
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
