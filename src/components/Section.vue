<template>
  <div class="section" :style="styled"></div>
</template>

<script>
export default {
  props: {
    color: {
      type: String,
      default: "black"
    },
    active: Boolean
  },
  computed: {
    styled() {
      return {
        background: this.color,
        display: this.active ? "block" : "none"
      };
    }
  }
};
</script>

<style lang="scss" scoped>
.section {
  height: 100vh;
  width: 100%;
  box-sizing: border-box;
  position: fixed;
  top: 0;
  left: 0;
  pointer-events: none;
  &::-webkit-scrollbar {
    display: none;
  }
}
</style>
