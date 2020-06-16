<template>
  <div>
    <ul>
      <li v-for="result in results" :key="result.id.videoId">
        {{ result.snippet.title }}
        <img :src="result.snippet.thumbnails.default.url" />
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "videoList",
  props: {
    results: Array,
  },
};
</script>

<style></style>
