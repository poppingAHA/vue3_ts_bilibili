<template>
    <van-tabs v-model:active="active">
        <van-tab title="推荐" name="recommend">
            <VideoRecommend/>
        </van-tab>        
        <van-tab title="评论" name="comment">
            <VideoComment/>
        </van-tab>        
    </van-tabs>
</template>
<script setup lang="ts">
import { ref } from 'vue';
import VideoRecommend from './video-recommend.vue';
import VideoComment from './video-comment.vue';

const active = ref('recommend')
</script>