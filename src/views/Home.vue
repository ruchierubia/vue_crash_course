<template>
  <div id="app">
    <AddTask v-on:add-task="addTask"/>
    <Tasks v-bind:tasks="tasks" v-on:del-task="deleteTask"/>
  </div>
</template>

<script>
import Tasks from '../components/Tasks';
import AddTask from '../components/AddTask';
import axios from 'axios';

  export default {
    name: 'Home',
    components: {
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
        axios.delete('https://jsonplaceholder.typicode.com/todos/${id}')
        .then( res => {
          console.log(res);
          this.tasks = this.tasks.filter(x => x.id != id);
        })
        .catch()
      },
      addTask(newTask) {
        const { title, completed } = newTask;        
        axios.post('https://jsonplaceholder.typicode.com/todos', {
          title,
          completed
        })
        .then(res => {
          console.log(res.data);
          this.tasks = [...this.tasks, res.data];
        })
        .catch(err => console.log(err));
      }
    },
    // 
    created() {
      axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
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
