<template>
    <div>
        <SearchBar @termChange="onTermChange"></SearchBar>
        <VideoList :videos="myVideoList"></VideoList>
    </div>
</template>

<script>

import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';

const API_KEY = 'AIzaSyBLyRVyyJvYbaCaKZ7PwY0Fob2TbrUPgJc';

export default {
  name: 'App',
  components: {
      SearchBar,
      VideoList
  },
  data() {
      return {
          myVideoList: []
      };
  },
  methods: {
      onTermChange: function(searchTerm) {
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
      }
  }
};
</script>