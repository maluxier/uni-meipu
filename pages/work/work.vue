<template>
	<view class="container">
		<view class="homework-list-section">
			<uni-list>
				<template v-for="(courseGroup, groupIndex) in homeworkData" :key="groupIndex">
					<uni-list-item direction="column" :border="false" :clickable="false">
						<template v-slot:body>
							<view class="course-group-header">
								<image :src="courseGroup.image" mode="aspectFill" class="course-group-image"></image>
								<text class="course-group-title">{{ courseGroup.title }}</text>
							</view>
						</template>
					</uni-list-item>
		
					<uni-list-item
						v-for="(exercise, exerciseIndex) in courseGroup.exercises"
						:key="groupIndex + '-' + exerciseIndex"
						:title="exercise.name"
						clickable
						@click="goWorkDetail(exercise.name)"
					></uni-list-item>
		
					<view v-if="groupIndex < homeworkData.length - 1" class="group-spacer"></view>
				</template>
			</uni-list>
		</view>
	</view>
		
</template>

<script setup>
import { ref } from 'vue';

	const homeworkData = ref([{
		title: 'Web前端开发',
		image: '/static/webDev.png', // 替换为你的图片路径
		exercises: [{
				name: '练习1: 初识uni-app'
			},
			{
				name: '事件练习'
			},
			{
				name: '函数'
			},
			{
				name: '流程控制语句'
			},
			{
				name: '运算符'
			},
		]
	},
	{
		title: 'Web开发基础',
		image: '/static/web.png', // 替换为你的图片路径
		exercises: [{
				name: '弹性布局练习'
			},
			{
				name: '盒子模型练习'
			},
			{
				name: '表单练习'
			},
			{
				name: 'CSS文字属性练习'
			},
			{
				name: '个人主页练习'
			},
			{
				name: 'HTML标签练习'
			},
		]
	}])

const goWorkDetail = (name) => {
	uni.navigateTo({
		url: '/pages/workDetail/workDetail?name=' + encodeURIComponent(name)
	})
}
</script>

<style>
	.container {
		background-color: #f8f8f8;
		min-height: 100vh; /* 确保背景色填充整个屏幕 */
		display: flex;
		flex-direction: column;
		justify-content: center;
		padding-bottom: env(safe-area-inset-bottom); /* 适配底部安全区 */
	}
	.homework-list-section {
		flex: 1; /* 占据剩余空间 */
		padding-top: 10px; /* 顶部与导航栏的间距 */
		margin: 20rpx;
		border-radius: 20rpx;
		overflow: hidden;
	}

	/* 课程分组标题 */
	.course-group-header {
		display: flex;
		align-items: center;
		padding: 10px 15px;
		background-color: #fff;	
	}

	.course-group-image {
		width: 40px;
		height: 40px;
		border-radius: 8px; /* 圆角 */
		margin-right: 10px;
	}

	.course-group-title {
		font-size: 16px;
		font-weight: bold;
		color: #333;
	}

	/* 每个课程分组之间留出间距 */
	.group-spacer {
		height: 10px;
		background-color: #f8f8f8;
	}

	/* 正在进行中的指示器圆点 */
	.in-progress-indicator {
		width: 8px;
		height: 8px;
		background-color: #FFC0CB; /* 粉色圆点 */
		border-radius: 50%;
		margin-left: 10px; /* 与文字的间距 */
	}
	
		/* 调整 uni-list-item 的一些默认样式，使其更符合设计 */
	uni-list-item {
		margin-bottom: 0 !important; /* 移除 uni-list-item 默认可能带的 margin */
	}
	.uni-list-item {
		padding-left: 0 !important; /* 确保 uni-list-item 的左边距可控 */
	}
</style>
