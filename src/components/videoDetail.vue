<template>
    <div class="col-md-8" v-if="video">
        <div class="embed-responsive embed-responsive-16by9">
            <iframe class="embed-responsive-item" :src="videoUrl"/>
        </div>
        <div class="detail">
            <h4>{{video.snippet.title}}</h4>
            <p>{{video.snippet.description}}</p>
        </div>
    </div>
</template>

<script>
export default {
    name:'videoDetail',
    props:['video'],
    computed:{
        videoUrl(){
            const { videoId } = this.video.id //const videoId = this.video.id.videoId
            //console.log(this.video.id)
            return `https://www.youtube.com/embed/${videoId}`
        }
    }
    
}
</script>

<style scoped>
.detail{
    margin-top: 10px;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
}
</style>