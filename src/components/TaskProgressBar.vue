<template>
    <div class="task-progress">
        <span class="progress-value">{{ progress }} %</span>
        <div class="progress-bar" :style="{ width: progress + '%'}"></div>
    </div>
</template>

<script>
export default {
    props: {
        tasks: Array
    },
    computed: {
        progress: function() {
            let progress = 0
            const total = this.tasks.length
            if(total > 0){
                const found = this.tasks.filter(t => t.class == 'done')
                const done = found.length

                progress = Math.round((100 * done)/total)
            }
            return progress;
        }
    },
}
</script>

<style>
    .task-progress{
        position: relative;
        width: 80%;
        border: 1px solid white;
        border-radius: 8px;
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-bottom: 15px;
    }
    .progress-bar {
        position: absolute;
        height: 100%;
        align-self: flex-start;
        background-color: #4CAF50;
        border-radius: 8px;
    }
    .progress-value {
        z-index: 1;
        font-size: 1.5rem;
    }
    
</style>
