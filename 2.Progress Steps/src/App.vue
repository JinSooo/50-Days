<template>
	<Step :currentIndex="currentIndex">
		<div
			:class="{ task, active: currentIndex >= index }"
			v-for="(task, index) in taskList"
			:key="index + task.desc"
			:task="task"
			@click="next(index, task)"
		>
			<div class="task-progress" :style="{ width: currentIndex >= index ? '100%' : '0' }"></div>
			<div class="show">
				{{ task.desc }}
			</div>
		</div>
	</Step>
</template>

<script setup lang="ts">
import Step from './components/Step/index.vue'
import { ref } from 'vue'
import { Task } from './types'

const taskList: Task[] = [
	{
		desc: 'Not Start',
	},
	{
		desc: 'Started',
	},
	{
		desc: 'Starting',
	},
	{
		desc: 'Ended',
	},
]

const currentIndex = ref(0)

const next = (index: number, task: Task) => {
	currentIndex.value = index
	console.log('%c ' + task.desc + ' ', 'background:#0ca6dc;padding:4px 10px;border-radius:3px;color:#fff')
}
</script>

<style scoped lang="less">
@import './assets/css/index.less';
@width: 70px;

.task {
	z-index: 9;
	position: relative;
	display: flex;
	justify-content: center;
	align-items: center;

	width: @width;
	height: @width;

	font-size: 12px;

	background-color: #eee;
	border-radius: 50%;

	overflow: hidden;
	cursor: pointer;
	transition: 0.3s 0.2s;

	.task-progress {
		position: absolute;
		z-index: -1;
		left: 0;
		width: 0%;
		height: @width;
		background-color: @primary;

		transition: 0.3s 0.2s;
	}

	.show {
		display: flex;
		justify-content: center;
		align-items: center;

		width: calc(@width - 10px);
		height: calc(@width - 10px);
		border-radius: 50%;
		background-color: #fff;
	}
}
.active {
	border-color: @primary;
	color: @primary;
}
</style>
