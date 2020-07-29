<template>
  <div class="home" @wheel="handleScroll">
    <Top :delta="deltaY" :scroll="isScrolling"></Top>
    <scroll-down></scroll-down>
  </div>
</template>

<script>
// @ is an alias to /src
import ScrollDown from "@/components/ScrollDown.vue";
import Top from "@/components/Top.vue";

export default {
  name: "Home",
  data: function() {
    return {
      isScrolling: false,
      deltaY: 0
    };
  },
  components: {
    Top,
    ScrollDown
  },
  methods: {
    handleScroll(event) {
      const deltaY = event?.deltaY;
      if (deltaY > 50 || deltaY < -50) {
        this.isScrolling = true;
      }
      this.deltaY = deltaY;
      // console.log(this.deltaY);
    },
    toggleScrolling() {
      this.isScrolling = !this.isScrolling;
    }
  },
  watch: {
    deltaY(old, newVal) {
      if (newVal > 50 || newVal < -50) {
        setTimeout(() => (this.isScrolling = false), 500);
      }
    },
    isScrolling(old, newVal) {
      if (!newVal) console.log("stop scrol");
    }
  }
};
</script>

<style lang="scss" scoped>
.home {
  width: 100vw;
  height: 100vh;
  overflow: scroll;
}
* {
  &::-webkit-scrollbar {
    display: none;
  }
}
</style>
