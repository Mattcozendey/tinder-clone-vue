<template>
  <div class="chooser">
    <Options v-on:response="sendResponse($event)" />
  </div>
</template>

<script>
import Options from "@/components/swipe-section/Options.vue";

export default {
  name: "Choose",
  components: { Options },
  methods: {
    sendResponse(event) {
      this.$emit("sendResult", event);
    }
  }
};
</script>

<style scoped>
.chooser {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 15%;
}
</style>