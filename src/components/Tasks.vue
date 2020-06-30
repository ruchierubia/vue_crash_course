<template>
    <div>
        <div v-bind:key ="task.id" v-for="task in tasks">
            <h3>{{task.title}}</h3>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Tasks',
    props: ['tasks']
}
</script>

<style scoped>

</style>