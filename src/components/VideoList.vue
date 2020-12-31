<template>
    <ul>
        <VideoListItem
            v-for="myVideo in videos"
            :video="myVideo"
            :key="myVideo.etag"
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
}
</script>

<style>

</style>