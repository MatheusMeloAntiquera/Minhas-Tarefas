<template>
    <div class="task" :class="[task.class]" @click="changeClass()">
        <span class="close" @click="deleteTask(index)">x</span>
        <p>{{ task.text }}</p>
    </div>
</template>

<script>
export default {
  props: {
    task: Object,
    deleteTask: Function,
    index:  Number
  },
  methods: {
      changeClass(){
        this.task.class = this.task.class == 'done' ? 'pending' : 'done';
      }
  },
};
</script>

<style>
</style>
