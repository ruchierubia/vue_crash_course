<template>
    <div>
     <form @submit="addTask">
        <input type="text" v-model="title" name="title" placeholder="Add task...">
        <input type="submit" value="Submit" class="btn">
     </form>
    </div>
</template>


<script>

export default {
    name: 'AddTask',
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTask(e) {
            e.preventDefault();         
            const newTask = {
                title: this.title,
                completed: false
            }
            // Emit to parent
            this.$emit('add-task', newTask);
            this.title = '';
        }
    }
}
</script>


<style scoped>
    form {
        display: flex;
    }

    input[type="text"] {
        flex: 10;
        padding: 5px;
    }

    input[type="submit"] {
        flex: 2;
    }
</style>