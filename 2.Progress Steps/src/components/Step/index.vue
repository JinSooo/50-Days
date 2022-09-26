<template>
	<div class="container">
		<div class="progress-container">
			<div class="progress"></div>
		</div>
		<slot></slot>
	</div>
</template>

<script setup lang="ts">
import { computed } from 'vue'

interface Props {
	currentIndex: number
}

const props = defineProps<Props>()

const progressWidth = computed(() => Math.floor(100 / 3) * props.currentIndex + '%')
</script>

<style scoped lang="less">
@import '../../assets/css/index.less';
.container {
	position: relative;
	display: flex;
	justify-content: space-between;
	align-items: center;

	width: 375px;
	.progress-container {
		position: absolute;
		width: 100%;
		height: 5px;

		border-radius: 5px;
		background-color: #eee;
		.progress {
			width: v-bind(progressWidth);
			height: 5px;

			background-color: @primary;
			transition: 0.3s;
		}
	}
}
</style>
