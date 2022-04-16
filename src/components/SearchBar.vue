<template>
  <section>
    <div>
      <font-awesome-icon class="icon" icon="fa-solid fa-magnifying-glass" />
      <input
        type="text"
        placeholder="Search Github username..."
        v-model="userName"
        @focus="resetInput()"
        v-bind:class="{ 'no-input': isThereAValidationError }"
      />
      <p v-if="isThereAValidationError" style="color: red">Error Message</p>
      <button @click="apiCall()">Search</button>
    </div>
  </section>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      isThereAValidationError: false,
      userName: "",
      user: {},
    };
  },
  methods: {
    apiCall() {
      axios
        .get("https://api.github.com/users/" + this.userName)
        .then((response) => {
          this.user = response.data;
          this.isThereAValidationError = false;
          this.$emit("userDataLanded", this.user);
        })
        .catch((error) => {
          console.warn(error);
          this.isThereAValidationError = true;
        });
    },
    resetInput() {
      this.isThereAValidationError = false;
      this.userName = "";
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
