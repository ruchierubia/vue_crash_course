<template>
    <div class="task-item" :class="{'is-complete' : task.completed}">
        <p>
            <input type="checkbox" v-on:change="markComplete">
            {{task.title}}
            <button @click="$emit('del-task', task.id)" class="del">x</button>
        </p>
    </div>
</template>

<script>
export default {
    name: 'TaskItem',
    props: ['task'],
    methods: {
        markComplete() {
            this.task.completed =!this.task.completed;
        }
    }
}
</script>

<style scoped>
    .task-item {
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }

    .is-complete {
        text-decoration: line-through;
    }

    .del {
        background: #ff0000;
        color: #ffff;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>