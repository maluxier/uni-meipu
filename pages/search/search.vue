<template>
	<view class="search-page">
		<view class="search-bar">
			<input class="search-input" placeholder="搜索课程/作业/应用" v-model="query" @confirm="doSearch" />
			<view class="search-btn" @click="doSearch">搜索</view>
		</view>

		<view class="history">
			<view class="history-header">
				<text class="history-title">历史记录</text>
				<text class="clear" @click="clearHistory">清空</text>
			</view>

			<view v-if="history.length" class="history-tags">
				<view class="tag" v-for="(h, idx) in history" :key="idx" @click="useHistory(h)">{{ h }}</view>
			</view>
			<view v-else class="empty">暂无历史记录</view>
		</view>
	</view>
</template>

<script setup>
import { ref, onMounted } from 'vue';
const query = ref('');
const history = ref([]);

onMounted(()=>{
  const h = uni.getStorageSync('search_history') || [];
  history.value = h;
});

const doSearch = ()=>{
  if(!query.value) return;
  let h = uni.getStorageSync('search_history') || [];
  h = h.filter(x=>x !== query.value);
  h.unshift(query.value);
  uni.setStorageSync('search_history', h.slice(0,10));
  history.value = h.slice(0,10);
  uni.showToast({title: '已搜索：' + query.value, icon: 'none'});
}

const useHistory = (h)=>{ query.value = h; doSearch(); }
const clearHistory = ()=>{ uni.removeStorageSync('search_history'); history.value = []; }
</script>

<style>
.search-page {
	min-height: 100vh;
	background: #f6f7fb;
	padding: 24rpx;
	box-sizing: border-box;
}

.search-bar {
	display: flex;
	align-items: center;
	background: #ffffff;
	border-radius: 18rpx;
	padding: 16rpx;
	box-shadow: 0 6rpx 18rpx rgba(0, 0, 0, 0.04);
}

.search-input {
	flex: 1;
	height: 72rpx;
	padding: 0 20rpx;
	background: #f7f8fc;
	border-radius: 14rpx;
	margin-right: 16rpx;
	box-sizing: border-box;
}

.search-btn {
	height: 72rpx;
	padding: 0 24rpx;
	border-radius: 14rpx;
	background: #007aff;
	color: #ffffff;
	display: flex;
	align-items: center;
	justify-content: center;
	font-size: 26rpx;
}

.history {
	margin-top: 24rpx;
	background: #ffffff;
	border-radius: 18rpx;
	padding: 24rpx;
	box-shadow: 0 6rpx 18rpx rgba(0, 0, 0, 0.04);
}

.history-header {
	display: flex;
	justify-content: space-between;
	align-items: center;
}

.history-title {
	font-size: 30rpx;
	font-weight: 700;
	color: #1f2937;
}

.history-tags {
	display: flex;
	flex-wrap: wrap;
	margin-top: 18rpx;
}

.tag {
	background: #f3f4f6;
	padding: 10rpx 18rpx;
	border-radius: 999rpx;
	margin: 0 16rpx 16rpx 0;
	font-size: 24rpx;
	color: #374151;
}

.clear {
	color: #ff4d4f;
	font-size: 24rpx;
}

.empty {
	margin-top: 18rpx;
	color: #9ca3af;
	font-size: 24rpx;
}
</style>
