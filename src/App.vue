<template>
  <div id="app">
    <SearchBar @termChange="onTermChange" />
    <VideoList />
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar.vue";
import VideoList from './components/VideoList.vue'

const API_KEY = "AIzaSyCO_XHjESguHaAsleRR9XXHXHha8gUSTqY";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList,
  },
  methods: {
    onTermChange(searchTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: searchTerm,
          },
        })
        .then((response) => console.log(response));
    },
  },
};
</script>

<style></style>
