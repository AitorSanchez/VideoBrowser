<template>
    <div class="container">
        <SearchBar @termChange="onTermChange"></SearchBar>
        <!--<div class="embed-responsive embed-responsive-16by9">
            <iframe class="embed-responsive-item" src="https://www.youtube.com/embed/PIh2xe4jnpk"></iframe>
        </div>-->
        <div class="row">
            <VideoDetail :video="selectedVideo"/>
            <VideoList
                :videos="myVideoList"
                @videoSelect="onVideoSelect"
            >
            </VideoList>
        </div>
    </div>
</template>

<script>

import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';


const API_KEY = 'AIzaSyBLyRVyyJvYbaCaKZ7PwY0Fob2TbrUPgJc';

export default {
  name: 'App',
  components: {
      SearchBar,
      VideoList,
      VideoDetail
  },
  data() {
      return {
          myVideoList: [],
          selectedVideo: null
      };
  },
  methods: {
      onTermChange(searchTerm) {
          axios.get('https://www.googleapis.com/youtube/v3/search', {
              params: {
                  key: API_KEY,
                  type: 'video',
                  part: 'snippet',
                  q: searchTerm
              }
          }).then(response => {
              this.myVideoList = response.data.items;
          });
      },
      onVideoSelect(video) {
          this.selectedVideo = video;
      }
  }
};
</script>