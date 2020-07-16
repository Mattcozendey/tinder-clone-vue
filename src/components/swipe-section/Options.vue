<template>
  <div class="options">
    <Dislike v-on:judged="sendResult($event)" />
    <Super-like v-on:judged="sendResult($event)" />
    <Like v-on:judged="sendResult($event)" />
  </div>
</template>

<script>
import Dislike from "@/components/swipe-section/Dislike.vue";
import SuperLike from "@/components/swipe-section/SuperLike.vue";
import Like from "@/components/swipe-section/Like.vue";

export default {
  name: "Options",
  components: { Dislike, SuperLike, Like },
  methods: {
    sendResult(event) {
      this.$emit("response", event);
    }
  }
};
</script>

<style scoped>
.options {
  display: flex;
  width: 55%;
  height: 100%;
}
</style>
