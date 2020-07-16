<template>
  <div class="navbar">
    <Profile v-on:clicked="setActive($event)" />
    <Swipe v-on:clicked="setActive($event)" />
    <Chat v-on:clicked="setActive($event)" />
  </div>
</template>

<script>
import Profile from "@/components/navbar/Navbar-Profile.vue";
import Swipe from "@/components/navbar/Navbar-Swipe";
import Chat from "@/components/navbar/Navbar-Chat.vue";

export default {
  name: "Navbar",
  components: {
    Profile,
    Swipe,
    Chat
  },
  methods: {
    setActive(query) {
      switch (query.id) {
        case "profile-navbar-item":
          query = Profile;
          break;
        case "swipe-navbar-item":
          query = Swipe;
          break;
        case "chat-navbar-item":
          query = Chat;
      }
      console.log(query);
      //console.table(query.props);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.navbar {
  width: 100%;
  height: 10%;
  display: flex;
  justify-content: center;
  align-items: center;
  border-bottom: 2px solid #f5f5f5;
}
</style>
