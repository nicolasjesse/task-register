<template>
    <div class="bar">
        <input class="input" type="text" placeholder="New task?">
        <button class="button" @click="sendTask">+</button>
    </div>
</template>

<script>
export default {
    props: {
        addTask: {
            type: Function,
            required: true,
        }
    },
    methods: {
        sendTask() {
            const input = document.querySelector('.input')
            this.addTask({ text: input.value, done: false })
            input.value = ''
        }
    }
}
</script>

<style scoped>
    .bar {
        display: flex;
        height: 30px;
        width: 280px;
        border: solid 1px white;
        border-radius: 5px;
        overflow: hidden;
        background-color: white;
        margin: 20px 0px;
    }

    .button {
        flex: 1;
        color: white;
        background-color: #0099FF;
        border: none;
        outline: none;
        font-weight: 900;
    }

    .button:active {
        background-color: #0077DD
    }

    .input {
        flex: 5;
        outline: none;
        background-color: rgb(42, 71, 89);
        font-size: 1.2em;
        font-weight: 400;
        border: solid 1px white;
        color: white;
    }
</style>