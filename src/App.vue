<script>
	// Components
	import ItemsCount from "./components/ItemsCount.vue";
	import TodooItem from "./components/TodooItem.vue";
	import NewTodoo from "./components/NewTodoo.vue";

	export default {
		components: {
			ItemsCount,
			TodooItem,
			NewTodoo
		},
		data() {
			return {
				tasks: [],
				taskCount: 0

			}
		},
		methods: {
			inCount($event){
				this.tasks.push($event);
				return this.taskCount = this.tasks.length;
			},
			deCount(i){
				this.tasks.splice(i, 1);
				return this.taskCount = this.taskCount - 1
			}
		}
	}

</script>

<template>
	<div class="container">
		<div class="row">
			<h1>To doo list in VUE.js</h1>
		</div>
		<div class="row">
			<ItemsCount :count="taskCount" />
		</div>
		<div class="todoo-list">
			<div class="row">
				<TodooItem 
					v-for="(task, i) in tasks" 
					:key="i" 
					:title="task.title" 
					:status="task.status" 
					:priority="task.priority" 
					:date="task.created_at"
					@removeItem="deCount(i)"
					/>
			</div>
		</div>
			<NewTodoo @taskItem="inCount"/>
	</div>
</template>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}

.todoo-list {
	width: 60%;
	margin: 0 auto;
}
</style>
