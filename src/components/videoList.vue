<template>
    <ul class="col-md-4 ml-auto list-group">
        <VideoListItem v-for="video in videos" :video="video" :key="video.etag" @videoSelect="onVideosSelect"></VideoListItem>
    </ul>
</template>

<script>
import VideoListItem from './videoListItem'
export default {
    name:'videoList',
    components:{
        VideoListItem
    },
    props:['videos'],
    methods:{
        onVideosSelect(video){
            this.$emit('videoSelect',video)
        }
    }
}
</script>

<style>

</style>