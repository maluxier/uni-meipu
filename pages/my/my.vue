<template>
	<view class="page">
		<view class="nav-area" :style="{ paddingTop: statusBarHeight + 'px' }">
			<view class="nav-row">
				<view class="scan-icon" aria-label="scan"></view>
			</view>
		</view>

		<view class="content">
			<view class="profile">
				<view class="avatar">
					<text class="avatar-letter">U</text>
				</view>
				<text class="name">张三</text>
			</view>

			<view class="menu-list">
				<view class="menu-item" v-for="item in menus" :key="item.label">
					<view class="menu-left">
						<text class="menu-icon" :style="{ color: item.color }">{{ item.icon }}</text>
						<text class="menu-label">{{ item.label }}</text>
					</view>
					<text class="menu-arrow">›</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script setup>
import { ref } from 'vue';

const systemInfo = uni.getSystemInfoSync();
const statusBarHeight = systemInfo.statusBarHeight || 0;

const menus = ref([
	{ label: '笔记', icon: '✎', color: '#4d79ff' },
	{ label: '收藏', icon: '★', color: '#d64545' },
	{ label: '成就', icon: '🏆', color: '#d4a62a' },
	{ label: '设置', icon: '⚙', color: '#7c7c7c' }
]);
</script>

<style>
.page {
	min-height: 100vh;
	background: #f2f2f2;
}

.nav-area {
	background: #f2f2f2;
}

.nav-row {
	height: 88rpx;
	padding: 0 24rpx;
	display: flex;
	align-items: center;
}

.scan-icon {
	width: 28rpx;
	height: 28rpx;
	border: 3rpx solid #333;
	border-radius: 6rpx;
	position: relative;
}

.scan-icon::before,
.scan-icon::after {
	content: '';
	position: absolute;
	width: 8rpx;
	height: 8rpx;
	border-top: 3rpx solid #333;
	border-left: 3rpx solid #333;
}

.scan-icon::before {
	top: -3rpx;
	left: -3rpx;
}

.scan-icon::after {
	right: -3rpx;
	bottom: -3rpx;
}

.content {
	min-height: calc(100vh - 120rpx);
	background: #fff;
	border-top-left-radius: 22rpx;
	border-top-right-radius: 22rpx;
	padding: 34rpx 24rpx 24rpx;
	box-sizing: border-box;
}

.profile {
	display: flex;
	flex-direction: column;
	align-items: center;
	padding-top: 6rpx;
	padding-bottom: 28rpx;
}

.avatar {
	width: 128rpx;
	height: 128rpx;
	border-radius: 50%;
	background: #4e8f3d;
	display: flex;
	align-items: center;
	justify-content: center;
}

.name {
	margin-top: 18rpx;
	font-size: 34rpx;
	color: #333;
}

.avatar-letter {
	font-size: 72rpx;
	color: #fff;
	line-height: 1;
	font-weight: 600;
}

.menu-list {
	margin-top: 8rpx;
}

.menu-item {
	height: 88rpx;
	padding: 0 10rpx;
	display: flex;
	align-items: center;
	justify-content: space-between;
	border-bottom: 1rpx solid #e6e6e6;
}

.menu-left {
	display: flex;
	align-items: center;
}

.menu-icon {
	width: 44rpx;
	font-size: 30rpx;
	margin-right: 14rpx;
	text-align: center;
}

.menu-label {
	font-size: 26rpx;
	color: #444;
}

.menu-arrow {
	font-size: 40rpx;
	color: #bbb;
}
</style>
