<template>
  <div class="swipe-wrapper">
    <card v-on:judged="sendResult($event)" />
  </div>
</template>

<script>
import Card from "@/components/swipe-section/Card.vue";
export default {
  name: "Swipe",
  components: { Card },
  methods: {
    sendResult(event) {
      this.$emit("sendResult", event);
    }
  }
};
</script>

<style scoped>
.swipe-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 75%;
}
</style>