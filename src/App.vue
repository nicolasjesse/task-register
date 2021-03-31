<template>
	<div id="app">
		<h1>Tasks</h1>
		<progress-bar :progress="progress"/>
		<task-input :addTask="addTask"/>
		<div class="tasks">
			<template v-for="task in tasks">
				<task :taskObject="task" :allTasks="tasks" :key="task.text"/>
			</template>
		</div>
	</div>
</template>

<script>
import ProgressBar from '@/components/ProgressBar'
import TaskInput from '@/components/TaskInput'
import Task from '@/components/Task'

export default {
	components: {
		ProgressBar, TaskInput, Task
	},
	data() {
		return {
			tasks: [],
		}
	},
	computed: {
		progress() {
			let count = 0
			this.tasks.forEach(e => {
				e.done ? count++ : null
			})
			return (count/this.tasks.length)*100 || 0
		}
	},
	methods: {
		addTask(task) {
			this.tasks.push(task)
		}
	},
	created() {
		this.$on('deleteTask', task => {
			this.tasks = this.tasks.filter(obj => {
				return task != obj
			})
		})
	}
}
</script>

<style>
	body {
		font-family: 'Lato', sans-serif;
		background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
		color: #FFF;
	}

	#app {
		display: flex;
		flex: 1;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 100vh;
	}

	#app h1 {
		margin-bottom: 5px;
		font-weight: 300;
		font-size: 3rem;
	}

	.tasks {
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
		width: 95%;
	}
</style>
