<template>
  <div class="grid-wrapper">
    <div class="col-avatar">
      <img :src="userData.avatar_url" alt="user avatar" />
    </div>
    <div class="col-head">
      <h1>{{ userData.name }}</h1>
    </div>
    <div class="col-joined">
      <h4>{{ dateManipulation }}</h4>
    </div>
    <div class="col-username">
      <h3>
        <a :href="'https://github.com/' + userData.login" target="new">{{
          userData.login
        }}</a>
      </h3>
    </div>
    <div class="col-bio">
      <p>{{ userData.bio }}</p>
    </div>
    <div class="col-stats">
      <div>
        <h3>Repos</h3>
        <h2>{{ userData.public_repos }}</h2>
      </div>
      <div>
        <h3>Followers</h3>
        <h2>{{ userData.followers }}</h2>
      </div>
      <div>
        <h3>Following</h3>
        <h2>{{ userData.following }}</h2>
      </div>
    </div>
    <div class="col-more-1">More Information 1</div>
    <div class="col-more-2">More Information 2</div>
  </div>
</template>

<script>
export default {
  props: {
    userData: {
      type: Object,
      default: null,
    },
  },
  computed: {
    dateManipulation() {
      const monthString = [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December",
      ];
      const extractedDate = new Date(this.userData.created_at);
      let day = extractedDate.getDate();
      let year = extractedDate.getFullYear();
      let month = extractedDate.getMonth();
      return day + ". " + monthString[month] + " " + year;
    },
  },
};
</script>

<style lang="scss" scoped>
h1,
h2,
h3,
h4,
p {
  color: #fff;
  font-family: "Space Mono", monospace, sans-serif;
}
h1 {
  font-size: 26px;
  font-weight: bold;
  line-height: 38px;
}
h2 {
  font-size: 22px;
  font-weight: bold;
  line-height: 33px;
}
h3 {
  color: #0079ff;
  font-size: 16px;
  line-height: 24px;
}
h4 {
  font-size: 13px;
  line-height: 20px;
}
p {
  font-size: 15px;
  line-height: 25px;
}
a,
a:active,
a:visited {
  color: #0079ff;
  text-decoration: none;
}
a:hover {
  text-decoration: underline;
}
.grid-wrapper {
  display: grid;
  grid-template-columns: 117px repeat(2, 1fr);
  grid-template-rows: auto;
  gap: 10px;
  padding: 48px;
  background-color: #1e2a47;
  border-radius: 15px;
}
.col-avatar {
  grid-column: 1;
  grid-row: 1 / 6;
}
.col-avatar img {
  width: 100%;
  border-radius: 100%;
}
.col-head {
  grid-column: 2;
  grid-row: 1;
  text-align: left;
}
.col-joined {
  grid-column: 3;
  grid-row: 1;
  display: flex;
  align-items: center;
  justify-content: flex-end;
}
.col-username {
  grid-column: 2 / 3;
  grid-row: 2;
  text-align: left;
}
.col-bio {
  grid-column: 2 / 4;
  grid-row: 3;
  text-align: left;
}
.col-stats {
  grid-column: 2 / 4;
  grid-row: 4;
  padding: 15px 32px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  background-color: #141d2f;
  border-radius: 10px;
  text-align: left;
}
.col-more-1 {
  grid-column: 2;
  grid-row: 5;
}
.col-more-2 {
  grid-column: 3;
  grid-row: 5;
}
</style>
