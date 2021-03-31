<template>
    <div class="bar">
        <div class="progress" :style="progressWidth">
        </div>
        <div class="text">
            {{ progress.toFixed(0) }}%
        </div>
    </div>
</template>

<script>
export default {
    computed: {
        progressWidth () {
            return {
                width: this.progress + '%'
            }
        }
    },
    props: {
        progress: {
            type: Number,
            default: 0
        }
    }
}
</script>

<style scoped>
    .bar {
        margin: 5px 0px 15px 0px;
        height: 20px;
        width: 80%;
        border: solid 1px #AAA;
        border-radius: 5px;
        position: relative;
    }
    .progress {
        position: absolute;
        height: 20px;
        background-color: green;
        overflow: visible;
        bottom: 0;
    }
    .text {
        position: absolute;
        top: 0;
        right: 49%;
    }
</style>