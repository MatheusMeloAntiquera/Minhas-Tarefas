<template>
    <div class="tasks-grid">
        <p class="no-task" v-if="tasks.length == 0">Sua vida está em dia :)</p>
        <Task v-else v-for="(task, index) in tasks" :key="task.text" :task="task" :index="index" :deleteTask="deleteTask">
        </Task>
    </div>
</template>

<script>
import Task from './Task.vue'

export default {
    props: [
        'tasks'
    ],
    components: { Task },
    methods: {
        deleteTask(index){
         this.tasks.splice(index, 1)
         localStorage.setItem('tasks',JSON.stringify(this.tasks))
        }
    },
}
</script>

<style>
    .tasks-grid{
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }

    .task {
        position: relative;
        box-sizing: border-box;
        width: 350px;
        height: 150px;
        padding: 10px;
        border-radius: 8px;
        font-size: 2rem;
        font-weight: 300;
        cursor: pointer;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .tasks-grid .task {
        margin: 10px;
    }

    .pending{
        border-left: 12px solid #B73229;
        background-color: #F44336;
    }

    .no-task{
        color: #AAA;
        font-size: 1.7rem;
    }
    
    .done{
        color: #DDD;
        border-left: 12px solid #0A8F08;
        background-color: #4CAF50;
        text-decoration: line-through;
    }

    .close {
        position: absolute;
        right: 10px;
        top: 10px;
        font-size: 0.9rem;
        font-weight: 600;
        height: 20px;
        width: 20px;
        border-radius: 10px;
        display: flex;
        justify-content: center;
    }

    .done .close {
        background-color: #0A8F08;
    }

    .pending .close {
        background-color: #B73229;
    }
</style>
