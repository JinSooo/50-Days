<template>
	<PictureExhibition
		v-for="(pic, index) in picData"
		:key="index + pic.picPath"
		:pic="pic"
		:index="index"
		:currentIndex="currentIndex"
		@click="show(index)"
	/>
</template>

<script setup lang="ts">
import { reactive, ref } from 'vue'
import PictureExhibition from './components/PictureExhibition/index.vue'
import { PicData } from './types'

// 图片路径
const imgPath = '/src/assets/imgs/'

const picData: PicData[] = reactive([
	{
		picPath: imgPath + '1.jpg',
		desc: 'pic1',
	},
	{
		picPath: imgPath + '2.jpg',
		desc: 'pic2',
	},
	{
		picPath: imgPath + '3.png',
		desc: 'pic3',
	},
	{
		picPath: imgPath + '4.jpeg',
		desc: 'pic4',
	},
	{
		picPath: imgPath + '5.jpeg',
		desc: 'pic5',
	},
	{
		picPath: imgPath + '6.jpeg',
		desc: 'pic6',
	},
])

const currentIndex = ref(0)

const show = (index: number) => {
	currentIndex.value = index
}
</script>

<style scoped></style>
