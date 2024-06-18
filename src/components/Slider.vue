<template>
    <div class="slider">
      <div class="slider-wrapper" ref="sliderWrapper">
        <div v-for="(item, index) in items" :key="index" class="slider-item">
          <img :src="item.image" alt="Slider Image">
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'SliderVue',
    props: {
      items: {
        type: Array,
        required: true
      }
    },
    mounted() {
      this.setupSlider();
    },
    methods: {
      setupSlider() {
        const sliderWrapper = this.$refs.sliderWrapper;
        let isDragging = false;
        let startPosition = 0;
        let currentTranslate = 0;
        let prevTranslate = 0;
        let animationID = 0;
  
        // Touch events
        sliderWrapper.addEventListener('touchstart', touchStart);
        sliderWrapper.addEventListener('touchmove', touchMove);
        sliderWrapper.addEventListener('touchend', touchEnd);
        sliderWrapper.addEventListener('touchcancel', touchCancel);
  
        function touchStart(event) {
          startPosition = event.touches[0].clientY;
          isDragging = true;
          animationID = requestAnimationFrame(animation);
          sliderWrapper.style.transition = 'none';
        }
  
        function touchMove(event) {
          if (!isDragging) return;
          const currentPosition = event.touches[0].clientY;
          currentTranslate = prevTranslate + currentPosition - startPosition;
        }
  
        function touchEnd() {
          cancelAnimationFrame(animationID);
          isDragging = false;
          const threshold = 100;
          if (currentTranslate > threshold) {
            // Swipe down
            currentTranslate = prevTranslate + 100;
          } else if (currentTranslate < -threshold) {
            // Swipe up
            currentTranslate = prevTranslate - 100;
          }
          sliderWrapper.style.transition = 'transform 0.3s ease-out';
          sliderWrapper.style.transform = `translateY(${currentTranslate}px)`;
          prevTranslate = currentTranslate;
        }
  
        function touchCancel() {
          cancelAnimationFrame(animationID);
          isDragging = false;
        }
  
        function animation() {
          sliderWrapper.style.transform = `translateY(${currentTranslate}px)`;
          if (isDragging) requestAnimationFrame(animation);
        }
      }
    }
  }
  </script>
  
  <style scoped>
  .slider {
    width: 100%;
    height: 300px; /* Adjust height as needed */
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
  