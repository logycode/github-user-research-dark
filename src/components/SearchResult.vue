<template>
  <div class="grid-wrapper">
    <div class="col-avatar">Image</div>
    <div class="col-head"><h1>Name</h1></div>
    <div class="col-joined"><h4>joined</h4></div>
    <div class="col-username"><h3>username</h3></div>
    <div class="col-bio"><p>Biography</p></div>
    <div class="col-stats">Stats</div>
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
.grid-wrapper {
  display: grid;
  grid-template-columns: 117px repeat(2, 1fr);
  grid-template-rows: auto;
  gap: 10px;
  padding: 10px;
  background-color: #1e2a47;
  border-radius: 15px;
}
.col-avatar {
  grid-column: 1;
  grid-row: 1 / 6;
}
.col-head {
  grid-column: 2;
  grid-row: 1;
}
.col-joined {
  grid-column: 3;
  grid-row: 1;
}
.col-username {
  grid-column: 2 / 3;
  grid-row: 2;
}
.col-bio {
  grid-column: 2 / 3;
  grid-row: 3;
}
.col-stats {
  grid-column: 2 / 3;
  grid-row: 4;
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
