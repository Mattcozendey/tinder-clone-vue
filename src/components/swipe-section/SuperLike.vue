<template>
  <div class="option">
    <img @click="superliked" src="@/assets/chooser/super-like.png" alt srcset />
  </div>
</template>

<script>
export default {
  name: "SuperLike",
  methods: {
    superliked() {
      this.$emit("judged", "superliked");
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