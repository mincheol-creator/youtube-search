<template>
  <div id="app">
    <h1>Youtube 검색하기</h1>
    <SearchBar v-on:inputText="input" />
    <div id="searchResult">
      <VideoPlayer v-bind:results="results" />
      <VideoList v-bind:results="results" />
      <VideoItem :results="results" />
    </div>
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar.vue";
import VideoPlayer from "./components/VideoPlayer.vue";
import VideoList from "./components/VideoList.vue";
import VideoItem from "./components/VideoItem.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoPlayer,
    VideoList,
    VideoItem,
  },
  data() {
    return {
      results: [],
    };
  },
  methods: {
    input(userInput) {
      //1. 입력된 검색어를 가지고
      const baseURL = "https://www.googleapis.com/youtube/v3/search";
      const API_KEY = process.env.VUE_APP_YOUTUBE_API_KEY;
      console.log("검색어 입력 되었음");
      axios
        .get(baseURL, {
          params: {
            //key, part, q
            key: API_KEY,
            part: "snippet",
            type: "video",
            q: userInput,
            maxResults: 10,
          },
        })
        .then((response) => {
          console.log(response.data);
          this.results = response.data.items;
        });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#searchResult {
  display: flex;
}
</style>
