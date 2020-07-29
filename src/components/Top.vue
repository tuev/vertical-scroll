<template>
  <div class="top">
    <Section
      :color="color"
      v-for="(color, index) in items"
      :key="color"
      :active="isActive === index"
    ></Section>
  </div>
</template>

<script>
import Section from "@/components/Section.vue";

export default {
  props: {
    scroll: Boolean,
    delta: Number
  },
  data: function() {
    return {
      items: ["red", "blue", "green", "black", "yellow"],
      isActive: 0
    };
  },
  computed: {
    isScrollTop() {
      return this.scroll && this.delta < -50;
    },
    isScrollDown() {
      return this.scroll && this.delta > 50;
    }
  },
  components: {
    Section
  },
  watch: {
    isScrollTop(oldVal, newVal) {
      if (newVal) {
        console.log(
          Math.min(this.isActive + 1, this.items.length),
          "scroll top index"
        );
        this.isActive = Math.min(this.isActive + 1, this.items.length - 1);
      }
    },
    isScrollDown(oldVal, newVal) {
      if (newVal) {
        console.log(Math.max(this.isActive - 1, 0), "scroll down index");
        this.isActive = Math.max(this.isActive - 1, 0);
      }
    }
  }
};
</script>

<style>
.top {
  z-index: 2;
  overflow: hidden;
  position: fixed;
  height: 100%;
  height: 100vh;
  width: 100%;
}
</style>
