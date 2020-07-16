<template>
  <router-link class="nav-item" to="/profile">
    <span v-on:click="clicked()">
      <!--<img
        v-if="active == true"
        id="profile-navbar-item"
        src="@/assets/navbar/profile-active.png"
        alt
        srcset
      />-->
      <img id="profile-navbar-item" src="@/assets/navbar/profile-inactive.png" alt srcset />
    </span>
  </router-link>
</template>

<script>
export default {
  name: "Profile",
  props: ["QUERY"],
  methods: {
    clicked() {
      const QUERY = document.querySelector("#profile-navbar-item");
      this.$emit("clicked", QUERY);
    }
  }
};
</script>

<style scoped>
.nav-item {
  flex: 1.75;
  height: 100%;
}
span {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
}
</style>
