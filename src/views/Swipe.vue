<template>
  <div class="swiper-wrapper">
    <Swipe v-on:sendResult="getResult($event, 'swipe')" />
    <Choose v-on:sendResult="getResult($event, 'menu')" />
  </div>
</template>

<script>
import Swipe from "@/components/swipe-section/Swipe.vue";
import Card from "@/components/swipe-section/Card.vue";
import Choose from "@/components/swipe-section/Choose.vue";

export default {
  components: { Swipe, Choose },
  methods: {
    getResult(event, method) {
      console.log("o resultado é..." + event);
      if (method == "menu") {
        Card.methods.autoSwipe(event);
      }
    }
  }
};
</script>
<style scoped>
.swiper-wrapper {
  width: 100%;
  height: 100%;
}
</style>
