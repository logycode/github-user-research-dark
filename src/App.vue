<template>
  <div id="app">
    <header>
      <h1>devfinder</h1>
      <div>
        <button @click="toggleColorMode()">light</button>
        <font-awesome-icon icon="fa-solid fa-sun" />
      </div>
    </header>
    <main>
      <search-bar
        class="search-bar"
        @userDataLanded="processUserData"
      ></search-bar>
      <search-result
        class="search-result"
        :userData="userData"
        v-if="userData"
      ></search-result>
    </main>
  </div>
</template>

<script>
import SearchBar from "@/components/SearchBar.vue";
import SearchResult from "@/components/SearchResult.vue";

export default {
  data() {
    return {
      userData: null,
    };
  },
  components: {
    SearchBar,
    SearchResult,
  },
  methods: {
    toggleColorMode() {
      console.log("switch to mode");
    },
    processUserData(data) {
      this.userData = data;
    },
  },
};
</script>

<style lang="scss">
body {
  background-color: #141d2f;
}
#app {
  font-family: "Space Mono", monospace, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
header {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  margin: 144px auto 0;
  width: 730px;
}
button {
  background-color: #141d2f;
  border: none;
  color: white;
  font-family: inherit;
  cursor: pointer;
}
.search-bar {
  margin: 36px auto 0;
  width: 730px;
}
.search-result {
  margin: 24px auto;
  width: 730px;
}
</style>
