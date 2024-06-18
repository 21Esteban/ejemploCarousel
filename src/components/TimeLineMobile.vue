<template>
  <div class="contenedorDeTodo">
    <div class="slider">
      <div class="slider-wrapper" ref="sliderWrapper">
        <div
          v-for="item in fakeData"
          :key="item.id"
          class="slider-item"
        >
          <img
            :src="item.image"
            :alt="'Slider Image ' + item.id"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      fakeData: [
        { id: 1, image: "https://via.placeholder.com/200/92c952" },
        { id: 2, image: "https://via.placeholder.com/150/771796" },
        { id: 3, image: "https://via.placeholder.com/150/24f355" },
        { id: 4, image: "https://via.placeholder.com/150/d32776" },
        { id: 5, image: "https://via.placeholder.com/150/f66b97" },
        { id: 6, image: "https://via.placeholder.com/150/56a8c2" },
        { id: 7, image: "https://via.placeholder.com/150/b0f7cc" },
        { id: 8, image: "https://via.placeholder.com/150/54176f" },
        { id: 9, image: "https://via.placeholder.com/150/51aa97" },
        { id: 10, image: "https://via.placeholder.com/150/810b14" }
      ],
      isDragging: false,
      startPosition: 0,
      currentTranslate: 0,
      prevTranslate: 0,
      animationID: 0
    };
  },
  mounted() {
    this.setupSlider();
  },
  methods: {
    setupSlider() {
      const sliderWrapper = this.$refs.sliderWrapper;

      sliderWrapper.addEventListener("touchstart", this.touchStart);
      sliderWrapper.addEventListener("touchmove", this.touchMove);
      sliderWrapper.addEventListener("touchend", this.touchEnd);
      sliderWrapper.addEventListener("touchcancel", this.touchCancel);
    },
    touchStart(event) {
      this.startPosition = event.touches[0].clientY;
      this.isDragging = true;
      this.animationID = requestAnimationFrame(this.animation);
      this.$refs.sliderWrapper.style.transition = "none";
    },
    touchMove(event) {
      if (!this.isDragging) return;
      const currentPosition = event.touches[0].clientY;
      this.currentTranslate =
        this.prevTranslate + currentPosition - this.startPosition;
    },
    touchEnd() {
      cancelAnimationFrame(this.animationID);
      this.isDragging = false;
      const threshold = 100;
      if (this.currentTranslate > threshold) {
        this.currentTranslate = this.prevTranslate + 100;
      } else if (this.currentTranslate < -threshold) {
        this.currentTranslate = this.prevTranslate - 100;
      }
      this.$refs.sliderWrapper.style.transition =
        "transform 0.3s ease-out";
      this.$refs.sliderWrapper.style.transform = `translateY(${this.currentTranslate}px)`;
      this.prevTranslate = this.currentTranslate;
    },
    touchCancel() {
      cancelAnimationFrame(this.animationID);
      this.isDragging = false;
    },
    animation() {
      this.$refs.sliderWrapper.style.transform = `translateY(${this.currentTranslate}px)`;
      if (this.isDragging) requestAnimationFrame(this.animation);
    }
  }
};
</script>

<style scoped>
.contenedorDeTodo {
  width: 100%;
  height: 400px; /* Ajusta la altura según tus necesidades */
  overflow: hidden;
}

.slider {
  width: 100%;
  height: 100%;
  overflow: hidden;
}

.slider-wrapper {
  display: flex;
  transition: transform 0.3s ease;
}

.slider-item {
  flex: 0 0 100%;
  height: 100%;
  overflow: hidden;
}

.slider-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>
