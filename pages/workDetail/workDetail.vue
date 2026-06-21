<template>
	<view class="page">
		<view class="blank"></view>
	</view>
</template>

<script setup>
import { ref } from 'vue';
import { onLoad } from '@dcloudio/uni-app';

const title = ref('作业详情');

onLoad((options) => {
	if (options && options.name) {
		title.value = decodeURIComponent(options.name);
	}

	uni.setNavigationBarTitle({ title: title.value });
	uni.setNavigationBarColor({
		frontColor: '#000000',
		backgroundColor: '#f2f2f2',
		animation: {
			duration: 0,
			timingFunc: 'linear'
		}
	});
});
</script>

<style>
.page {
	min-height: 100vh;
	background: #ffffff;
}

.blank {
	height: 100vh;
	background: #ffffff;
}
</style>
