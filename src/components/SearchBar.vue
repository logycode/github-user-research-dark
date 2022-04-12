<template>
  <div>
    <font-awesome-icon class="icon" icon="fa-solid fa-magnifying-glass" />
    <input
      type="text"
      placeholder="Search Github username..."
      v-model="userName"
      id="user-input"
      @focus="reset()"
    />
    <button @click="apiCall()">Search</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      userName: "",
      user: {},
    };
  },
  methods: {
    apiCall() {
      const element = document.getElementById("user-input");
      if (this.userName === "") {
        element.classList.add("no-input");
        element.placeholder = "Please fill in user name you want to search";
      } else {
        axios
          .get("https://api.github.com/users/" + this.userName)
          .then((response) => {
            this.user = response.data;
            this.$emit("userDataLanded", this.user);
          })
          .catch(function (error) {
            if (error.response.status === 404) {
              element.classList.add("no-input");
              element.value = "No results";
            }
          })
          .then(function () {
            // always excute
          });
      }
    },
    reset() {
      const element = document.getElementById("user-input");
      this.userName = "";
      this.user = null;
      element.value = "";
      element.classList.remove("no-input");
      element.placeholder = "Search Github username...";
      this.$emit("userDataLanded", this.user);
    },
  },
};
</script>

<style lang="scss" scoped>
div {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  border: none;
  border-radius: 15px;
  background-color: #1e2a47;
}
.icon {
  margin-left: 22px;
  width: 24px;
  height: 24px;
  color: #0079ff;
}
div input {
  width: 500px;
  outline: none;
  background-color: #1e2a47;
  border: none;
  color: white;
  font-size: 18px;
  font-family: "Space Mono", monospace, sans-serif;
}
div input::placeholder {
  color: #fff;
  font-family: "Space Mono", monospace, sans-serif;
}
.no-input {
  color: red;
  font-weight: bold;
}
.no-input::placeholder {
  color: red;
}
div button {
  width: 106px;
  height: 50px;
  border: none;
  border-radius: 10px;
  background-color: #0079ff;
  color: #fff;
  font-size: 16px;
  font-family: "Space Mono", monospace, sans-serif;
  font-weight: bold;
}
</style>
