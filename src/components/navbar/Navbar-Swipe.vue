<template>
  <router-link id="testando" class="nav-item" to="/">
    <span v-on:click="clicked()">
      <img id="swipe-navbar-item" src="@/assets/navbar/swipe-active.png" alt srcset />
    </span>
  </router-link>
</template>

<script>
export default {
  name: "Swipe",
  props: ["QUERY"],
  methods: {
    clicked() {
      const QUERY = document.querySelector("#swipe-navbar-item");
      this.$emit("clicked", QUERY);
    }
  }
};
</script>

<style scoped>
.nav-item {
  flex: 1;
  height: 100%;
}
span {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
