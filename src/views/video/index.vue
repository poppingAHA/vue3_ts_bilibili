<template>
    <!-- 头部组件 -->
    <AppHeader />
    <!-- 视频播放组件 -->
    <VideoPlay :videoInfo="videoInfo" />
    <!-- 视频详情组件 -->
    <VideoDetails :videoInfo="videoInfo"/>
    <!-- 推荐/评论按钮组件 -->
    <VideoButton/>
</template>
<script setup lang="ts">
import AppHeader from '@/components/app-header.vue';
import axios from 'axios';
import { ref } from 'vue';
import { useRoute } from 'vue-router';
import { IVideoInfo } from './types';
import VideoPlay from './components/video-play.vue';
import VideoDetails from './components/video-details.vue';
import VideoButton from './components/video-button.vue';

const videoInfo = ref<IVideoInfo>({})

const route = useRoute()

axios({
    url: '/videoDetail',
    method: 'get',
    // 根据路由对象的 id 参数发送请求获取对应的视频详情
    params: { id: route.params.id }
}).then(({ data }) => {
    videoInfo.value = data.result
    console.log('视频详情数据', data.result)
})
</script>
<style lang="less" scoped>
.video-info {
    padding: 3vw 2vw;
    border-bottom: 1px solid #ddd;

    .title {
        font-size: 4vw;
        line-height: 6vw;
        margin: 3vw 0;
    }

    .author-info {
        display: flex;
        align-items: center;
        font-size: 3vw;
        color: #999;

        .author {
            flex: 1;

            .author-avatar {
                width: 5vw;
                height: 5vw;
                object-fit: cover;
                border-radius: 50%;
                overflow: hidden;
                margin: 0 1vw;
                background: url(~@/assets/images/loading.png) no-repeat center #e7e7e7;
            }

            .author-name {
                color: #212121;
            }
        }

        >span {
            margin: 0 2vw;
        }

        .iconfont {
            font-size: 5vw;
            color: #757575;
            margin-right: 2vw;
        }
    }
}
</style>
    