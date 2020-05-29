<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <div class="row">
      <VideoDetail :video="selectedVideo"></VideoDetail>
      <VideoList :videos="videos" @videoSelect="onVideosSelects"></VideoList>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/searchBar';
import VideoList from './components/videoList';
import VideoDetail from './components/videoDetail';
const API_KEY = 'AIzaSyCZZ_DW9k5APmxKulkSS_ogkMMn5P3gjY0';

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data(){
    return{
      videos:[],
      selectedVideo:null
    }
  },
  created(){
    this.onTermChange(Math.floor(Math.random()*50));
    
  },
  methods:{
    onTermChange(searchTerm){
      axios.get('https://www.googleapis.com/youtube/v3/search',{
        params:{
          key:API_KEY,
          type:'video',
          part:'snippet',
          q:searchTerm
        }
      })
      .then(response => {
        this.videos = response.data.items
      })
    },
    onVideosSelects(video){
      this.selectedVideo = video;
    }
  }
}
</script>

<style>

</style>
