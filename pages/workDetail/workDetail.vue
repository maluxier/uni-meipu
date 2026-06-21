<template>
  <view class="work-detail">
    <view class="container">
      <text class="title">{{ title }}</text>
    </view>
  </view>
</template>

<script setup>
import { ref } from 'vue';
import { onLoad } from '@dcloudio/uni-app';
const title = ref('作业详情');

onLoad((options) => {
  if(options && options.name){
    title.value = decodeURIComponent(options.name);
  }
  uni.setNavigationBarTitle({ title: title.value });
});
</script>

<style>
.container{padding:20px}
.title{font-size:18px;font-weight:600}
</style>
