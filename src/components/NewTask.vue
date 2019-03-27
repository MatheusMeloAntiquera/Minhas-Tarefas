<template>
    <div class="new-task">
        <input type="text" placeholder="Nova tarefa?" class="form-element" v-model="text">
        <button @click="newTask()" class="form-element">+</button>
    </div>
</template>

<script>
export default {
    props: [
        'tasks'
    ],
    data() {
        return {
            text: ''
        }
    },
    methods: {
        newTask(){
            
            //Not allow to empty text 
            if(this.text !== ''){
                //Looking for tasks with the same text
                const found = this.tasks.filter(t => t.text == this.text)

                //If it wasn't found then create a new task
                if(found.length == 0){
                    const task = { text: this.text, class: 'pending'}
                    this.tasks.push(task)
                    
                    //Save the tasks array in localstorage
                    localStorage.setItem('tasks',JSON.stringify(this.tasks))
                }

                //Clear the input
                this.text = ''
            }            
        }
    },
}
</script>

<style>
    .new-task {
        margin: 35px;
    }

    input.form-element {
        background-color: #FFF2;
        width: 500px;
        border-top-left-radius: 8px;
        border-bottom-left-radius: 8px;   
    }

    button.form-element{
        border-left: none;
        border-top-right-radius: 8px;
        border-bottom-right-radius: 8px;
        background-color: #2196F3;
        cursor: pointer;
    }

    .form-element {
        outline: none;
        font-size: 2rem;
        padding: 5px 10px 8px;
        border: 1px solid #FFF;
        color: #FFF;
    }
</style>
