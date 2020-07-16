<template>
  <div class="option">
    <img @click="like" src="@/assets/chooser/like.png" alt srcset />
  </div>
</template>

<script>
export default {
  name: "Like",
  methods: {
    like() {
      this.$emit("judged", "liked");
    }
  }
};
</script>

<style scoped>
.option {
  display: flex;
  justify-content: center;
  align-items: center;
  flex: 1;
}
img {
  cursor: pointer;
}
</style>