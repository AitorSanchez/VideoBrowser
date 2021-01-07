<template>
    <ul class="list-group col-md-4">
        <VideoListItem
            v-for="myVideo in videos"
            :video="myVideo"
            :key="myVideo.etag"
            @videoSelect="onVideoSelect"
        >
        </VideoListItem>
    </ul>
</template>

<script>
import VideoListItem from './VideoListItem'

export default {
    name: 'VideoList',
    components: {
        VideoListItem
    },
    props: {
        videos: Array
    },
    methods: {
        onVideoSelect(video) {
            this.$emit('videoSelect', video);
        }
    }
}
</script>

<style>

</style>