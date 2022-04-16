<template>
  <div id="app" ref="body">
    <header>
      <h1>devfinder</h1>
      <!-- <p v-if="lightMode == true">No light mode available</p> -->
      <div v-if="lightMode == false">
        <button @click="toggleColorMode()">light</button>
        <font-awesome-icon icon="fa-solid fa-sun" />
      </div>
      <div v-if="lightMode == true">
        <button @click="toggleColorMode()">dark</button>
        <font-awesome-icon icon="fa-solid fa-moon" />
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
      lightMode: false,
      lightStyle: {
        "background-color": "white",
        color: "black",
      },
    };
  },
  components: {
    SearchBar,
    SearchResult,
  },
  methods: {
    toggleColorMode() {
      if (this.lightMode === false) {
        this.lightMode = true;
        // dark mode actived
        this.$refs.body.setAttribute("dark-mode", "0");
      } else {
        this.lightMode = false;
        // dark mode deactived
        this.$refs.body.setAttribute("dark-mode", "1");
      }
      console.log(this.lightMode);
    },
    processUserData(data) {
      this.userData = data;
    },
  },
};
</script>

<style lang="scss">
body {
  margin: 0;
}
#app {
  // I defined variables of default mode (light)
  --header-color: red;

  // other styles
  font-family: "Space Mono", monospace, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  background-color: #141d2f;
  min-height: 100vh;
}

// I defined variables of dark mode
#app[dark-mode="0"] {
  --header-color: #141d2f;
  background-color: white;
}

header {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  margin: 144px auto 0;
  width: 730px;
  color: var(--header-color);
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
  width: 730px-96px;
}
</style>
