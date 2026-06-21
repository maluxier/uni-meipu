<template>
	<view class="card">
		<view class="card-top">
			<image class="avatar" :src="post.avatar" mode="aspectFill"></image>
			<view class="meta">
				<text class="name">{{ post.name }}</text>
				<text class="date">{{ post.date }}</text>
			</view>
		</view>

		<view class="content">{{ post.content }}</view>

		<view v-if="post.images && post.images.length" class="image-grid" :class="['count-' + post.images.length]">
			<image
				v-for="(img, index) in post.images"
				:key="index"
				class="post-image"
				:src="img"
				mode="aspectFill"
			></image>
		</view>

		<view class="actions">
			<view class="action-item">
				<image class="action-icon action-icon-img" src="/static/like/like/dianzan.png" mode="aspectFit"></image>
				<text class="action-text">{{ post.likeCount }}</text>
			</view>
			<view class="action-item">
				<text class="action-icon">💬</text>
				<text class="action-text">{{ post.commentCount }}</text>
			</view>
			<view class="action-item">
				<text class="action-icon">⭐</text>
				<text class="action-text">{{ post.collectCount }}</text>
			</view>
		</view>
	</view>
</template>

<script setup>
defineProps({
	post: {
		type: Object,
		required: true
	}
});
</script>

<style>
.card {
	background: #ffffff;
	border-radius: 20rpx;
	padding: 24rpx;
	margin-top: 18rpx;
	box-shadow: 0 6rpx 18rpx rgba(0, 0, 0, 0.04);
}

.card-top {
	display: flex;
	align-items: center;
}

.avatar {
	width: 72rpx;
	height: 72rpx;
	border-radius: 50%;
	background: #f1f5f9;
}

.meta {
	display: flex;
	flex-direction: column;
	margin-left: 16rpx;
}

.name {
	font-size: 28rpx;
	font-weight: 600;
	color: #1f2937;
}

.date {
	margin-top: 6rpx;
	font-size: 22rpx;
	color: #9ca3af;
}

.content {
	margin-top: 18rpx;
	font-size: 26rpx;
	line-height: 1.7;
	color: #374151;
}

.image-grid {
	display: grid;
	gap: 12rpx;
	margin-top: 18rpx;
}

.image-grid.count-1 {
	grid-template-columns: 1fr;
}

.image-grid.count-2,
.image-grid.count-4 {
	grid-template-columns: repeat(2, 1fr);
}

.image-grid.count-3,
.image-grid.count-5,
.image-grid.count-6 {
	grid-template-columns: repeat(3, 1fr);
}

.post-image {
	width: 100%;
	height: 210rpx;
	border-radius: 14rpx;
	background: #f8fafc;
}

.actions {
	display: flex;
	justify-content: space-between;
	margin-top: 18rpx;
	padding-top: 14rpx;
	border-top: 1rpx solid #f1f5f9;
}

.action-item {
	display: flex;
	align-items: center;
	color: #6b7280;
	font-size: 24rpx;
}

.action-icon {
	margin-right: 8rpx;
}

.action-icon-img {
	width: 30rpx;
	height: 30rpx;
}
</style>
