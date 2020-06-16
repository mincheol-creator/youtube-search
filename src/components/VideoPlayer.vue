<template>
  <div v-if="results.length > 0">
    <iframe
      v-bind:src="`https://www.youtube.com/embed/${results[0].id.videoId}`"
    ></iframe>
  </div>
</template>

<script>
export default {
  name: "VideoPlayer",
  props: {
    results: Array,
  },
};
</script>

<style></style>
