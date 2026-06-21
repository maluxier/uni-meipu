<template>
  <view class="search-page">
    <view class="search-bar">
      <input class="search-input" placeholder="搜索课程/作业/应用" v-model="query" @confirm="doSearch" />
      <button class="search-btn" @click="doSearch">搜索</button>
    </view>
    <view class="history">
      <view class="history-header">
        <text>历史记录</text>
        <text class="clear" @click="clearHistory">清空</text>
      </view>
      <view class="history-tags">
        <view class="tag" v-for="(h, idx) in history" :key="idx" @click="useHistory(h)">{{h}}</view>
      </view>
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
.search-bar{display:flex;padding:12px;background:#fff;align-items:center}
.search-input{flex:1;padding:8px;border:1px solid #eee;border-radius:6px;margin:0 8px}
.search-btn{padding:6px 10px;background:#007AFF;color:#fff;border-radius:6px}
.history{padding:12px}
.history-header{display:flex;justify-content:space-between;align-items:center}
.history-tags{display:flex;flex-wrap:wrap;margin-top:10px}
.tag{background:#f0f0f0;padding:8px 12px;border-radius:16px;margin:6px}
.clear{color:#ff4d4f}
</style>
