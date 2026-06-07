<template>
	<view>
		<uni-list>
			<uni-list-item v-for="(message, index) in myMessages" :key="index" :title="message.name" :note="message.tip" :thumb="message.image" thumb-size="lg" :rightText="message.time"></uni-list-item>
		</uni-list>
	</view>
</template>

<script setup>
import { ref } from 'vue';

	const myMessages = ref([{
		name: '张三',
		tip: '待会一起去吃饭',
		time: '下午5：44',
		image: '/static/logo.png'
	},
	{
		name: '张三',
		tip: '待会一起去吃饭',
		time: '下午5：44',
		image: '/static/logo.png'
	},
	{
		name: '张三',
		tip: '待会一起去吃饭',
		time: '下午5：44',
		image: '/static/logo.png'
	},
	{
		name: '张三',
		tip: '待会一起去吃饭',
		time: '下午5：44',
		image: '/static/logo.png'
	},
	{
		name: '张三',
		tip: '待会一起去吃饭',
		time: '下午5：44',
		image: '/static/logo.png'
	},
	{
		name: '张三',
		tip: '待会一起去吃饭',
		time: '下午5：44',
		image: '/static/logo.png'
	}])
</script>

<style>
	.container{
		display: flex;
	}
</style>
