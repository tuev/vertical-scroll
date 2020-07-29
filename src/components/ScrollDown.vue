<template>
  <div class="scrollDown" @wheel="handleScroll">
    <div class="stDown js-link is_linkActive" data-v-5043487c="">
      <div class="barWrap" data-v-5043487c="" style="opacity: 1;">
        <div class="barInner" data-v-5043487c="" style=""></div>
      </div>
      <p
        class="en_upper"
        data-v-5043487c=""
        style="transform: translate(0px, 0px);"
      >
        SCROLL DOWN
      </p>
    </div>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      scrollPosition: 0
    };
  },

  methods: {
    handleScroll(event) {
      const deltaY = event?.deltaY;
      console.log(deltaY, "Y");
    }
  }
};
</script>

<style>
.scrollDown {
  width: 100%;
  height: 400vh;
  position: fixed;
  top: 0;
  left: 0;
  pointer-events: none;
  z-index: 3;
}

.barWrap {
  width: 2px;
  height: 8rem;
  margin: 0 auto 0.65rem;
  overflow: hidden;
}

.barInner {
  width: 100%;
  height: 100%;
  background: white;
  transform: translate3d(0px, 0px, 0px) scale(1);
  transform-origin: center bottom;
  animation: scale 3s;
  animation-iteration-count: infinite;
}

.stDown {
  position: absolute;
  bottom: 2rem;
  right: 2rem;
  left: auto;
}

.en_upper {
  writing-mode: vertical-rl;
  font-weight: 700;
  color: white;
}

@keyframes scale {
  0% {
    transform: translate3d(0px, -8rem, 0px) scale(0);
  }
  50% {
    transform: translate3d(0px, 0px, 0px) scale(1);
  }
  100% {
    transform: translate3d(0px, 8rem, 0px) scale(0);
  }
}
</style>
