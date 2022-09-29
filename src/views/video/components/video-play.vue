<template>
    <div class="video-play">
        <video controls class="video" :poster="videoInfo.poster" :src="videoInfo.videoSrc"></video>
    </div>
</template>
<script setup lang="ts">
import { PropType } from 'vue'

import { IVideoInfo } from '../types'

defineProps({
    videoInfo: {
        type: Object as PropType<IVideoInfo>,
        required: true
    }
})

</script>
<style lang="less" scoped>
.video-play {
    background-color: #000;
    .video {
        width: 100%;
        min-height: 210px;
    }
}
</style>