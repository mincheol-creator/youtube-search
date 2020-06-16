<template>
  <div>
    <input v-model="userInput" @keypress.enter="inputText" type="text" />
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  methods: {
    inputText() {
      this.$emit("inputText", this.userInput);
    },
  },
  data() {
    return {
      userInput: "",
    };
  },
};
</script>

<style></style>
