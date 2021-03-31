<template>
    <div class="task" 
        @click="taskObject.done = !taskObject.done" 
        :style="backgroundToggle">
            {{ taskObject.text }}
        <div class="closeButton"
            @click="deleteTask"
            :style="closeButtonToggle">
            x</div>
    </div>
</template>

<script>
export default {
    props: {
        taskObject: {
            type: Object,
            required: true
        }
    },
    computed: {
        backgroundToggle() {
            return this.taskObject.done ? {
                backgroundColor: 'green',
                textDecoration: 'line-through',
                borderLeft: 'solid 10px #006600'
            } : {
                backgroundColor: '#EE1100',
                borderLeft: 'solid 10px #882222'
                }
        },
        closeButtonToggle() {
            return this.taskObject.done ? {
                backgroundColor: '#006600'
            } : {
                backgroundColor: '#882222'
            }
        }
    },
    methods: {
        deleteTask() {
            this.$parent.$emit('deleteTask', this.taskObject)
            this.$el.parentNode.removeChild(this.$el);
            this.$destroy()
        }
    }
}
</script>

<style scoped>
    .task {
        position: relative;
        font-family: 'Lato', sans-serif;
        font-weight: 200;
        width: 16vw;
        margin: 5px 10px;
        height: 80px;
        border-radius: 5px;
        text-align: center;
        vertical-align: middle;
        line-height: 80px;
        overflow: hidden;
        user-select: none;
    }

    .closeButton {
        position: absolute;
        top: 0;
        right: 0;
        display: inline;
        height: 15px;
        width: 15px;
        text-align: center;
        vertical-align: center;
        border-radius: 5px;
        line-height: 13px;
        font-size: 0.7em;
    }
</style>