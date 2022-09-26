<template>
	<div
		class="exhibition"
		:style="{ 'background-image': `url(${props.pic.picPath})` }"
		:class="props.currentIndex === props.index ? 'show' : ''"
	>
		{{ props.pic.desc }}
	</div>
</template>

<script setup lang="ts">
import { PicData } from '../../types'

interface Props {
	pic: PicData
	index: number
	currentIndex: number
}

const props = defineProps<Props>()
</script>

<style scoped lang="less">
@width: 100px;
.exhibition {
	margin: 10px;
	padding: 10px;
	width: @width;
	height: 90vh;
	line-height: 90vh;

	text-align: center;
	color: #fff;
	font-size: 1.2rem;
	border-radius: 20px;

	background-position: 50%;
	background-size: cover;
	background-repeat: no-repeat;
	cursor: pointer;
	transition: 0.5s;

	flex: 0.5 1;

	&.show {
		flex: 5 1;
	}
}
</style>
