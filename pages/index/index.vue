<template>
	<view class="serch">
		<input  class="input" type="text" placeholder="搜索"/>
	</view>
	<view class="section">
		<view class="section-head">
			<view class="indicator-icon"></view>
			<text class="section-title">我的应用</text>
		</view>
		<view class="app-gird">
			<view class="app-item" v-for="(app, index) in myApps" :key="index">
				<view class="item-bg" :style="{backgroundColor: app.color}">
					<image :src="app.image" mode="aspectFill" class="app-img"></image>
				</view>
				<text class="app-name">{{app.name}}</text>
			</view>
		</view>
		<view class="section-bottom">
			<text>查看更多</text>
		</view>
	</view>
	<view class="section">
		<view class="section-head">
			<view class="indicator-icon"></view>
			<text class="section-title">我的课程</text>
		</view>
		<uni-list>
			<uni-list-item v-for="(course, index) in myCourses" :key="index" :title="course.title" :note="course.teacher" :thumb="course.image" thumb-size="lg" :rightText="course.status"></uni-list-item>
			
		</uni-list>
		<view class="section-bottom">
			<text>查看更多</text>
		</view>
	</view>
</template>

<script setup>
import { ref } from 'vue';

	const myApps = ref([{
		name: '我的课程',
		color: '#5d73ff',
		image: '/static/courses.png'
	},
	{
		name: '数据分析',
		color: '#69d9aa',
		image: '/static/analysis.png'
	},
	{
		name: '我的课表',
		color: '#5d73ff',
		image: '/static/schedule.png'
	},
	{
		name: '代办',
		color: '#69d9aa',
		image: '/static/toDO.png'
	},
	{
		name: '成就勋章',
		color: '#69d9aa',
		image: '/static/achievement.png'
	},
	{
		name: '我的考试',
		color: '#5d73ff',
		image: '/static/exam.png'
	},
	{
		name: '讲座',
		color: '#69d9aa',
		image: '/static/lecture.png'
	},
	{
		name: '笔记',
		color: '#69d9aa',
		image: '/static/note.png'
	},
	])
	
	const myCourses = ref([{
		title: 'Web前端开发',
		teacher: '陈星宇',
		status: '学习中',
		image: '/static/webDev.png'
	},
	{
		title: '互联网开发进阶：移动端应用开发进阶',
		teacher: '程思慧',
		status: '学习中',
		image: '/static/appDev.png'
	},
	{
		title: 'Web开发基础',
		teacher: '黄小平',
		status: '已完成',
		image: '/static/web.png'
	}])
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.serch{
		display: flex;
		width: 100%;
		height: 80rpx;
		padding: 10rpx 0rpx;
		justify-content: center;
	}
	.input{
		border: 2rpx solid #a8a8a8;
		border-radius: 10rpx;
		width: 90%;
		height: 80rpx;
	}
	.section{
		background-color: #ffffff;
		padding: 15px;
		border-bottom: 1px solid #eee;
	}
	.section-head{
		display: flex;
		align-items: center;
	}
	.indicator-icon{
		width: 4px; /* 蓝色小图标的宽度 */
		height: 16px; /* 蓝色小图标的高度，与字体高度大致匹配 */
		background-color: #007AFF; /* 蓝色 */
		margin-right: 8px; /* 小图标和文字之间的间距 */
		border-radius: 2px;
	}
	.section-title{
		font-size: 16px;
		font-weight: bold;
	}
	.section-bottom{
		display: flex;
		justify-content: center;
	}
	
	.app-gird{
		display: grid;
		grid-template-columns: repeat(4, 1fr); 
		gap: 15px 0; 
		text-align: center;
		margin-bottom: 15px;
		margin-left: 20rpx;
	}
	.app-item{
		display: flex;
		flex-direction: column;
		align-items: center;
		margin-top: 10rpx;
		margin-right: 40rpx;
	}
	.item-bg{
		display: flex;
		align-items: center;
		border-radius: 20rpx;
		padding: 20rpx;
		width: 50rpx;
		height: 50rpx;
		overflow: hidden;
	}
	.app-img{
		width: 100%; 
		height: 100%;
		border-radius: 12px;
		margin-bottom: 5px;
	}
	.app-name{
		margin-top: 10rpx;
		font-size: 12px;
		color: #333;
	}
</style>
