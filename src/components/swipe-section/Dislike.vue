<template>
  <div class="option">
    <img @click="dislike" src="@/assets/chooser/dislike.png" alt srcset />
  </div>
</template>

<script>
export default {
  name: "Dislike",
  methods: {
    dislike() {
      this.$emit("judged", "disliked");
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