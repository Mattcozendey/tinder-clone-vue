<template>
  <router-link class="nav-item" to="/chat">
    <span v-on:click="clicked()">
      <img id="chat-navbar-item" src="@/assets/navbar/chat-inactive.png" alt srcset />
    </span>
  </router-link>
</template>

<script>
export default {
  name: "Chat",
  props: ["QUERY"],
  methods: {
    clicked() {
      const QUERY = document.querySelector("#chat-navbar-item");
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
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
