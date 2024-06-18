<template>
  <div class="contenedor-padre">
    <div class="main">
      <VueSlickCarousel
        :arrows="false"
        :dots="true"
        :vertical="true"
        style="height: 100%"
      >
        <div v-for="item in fakeData" :key="item.id" class="carousel-item">
          <div class="item-content">
            <div class="item-inner">
              <h3>{{ item.title }}</h3>
              <p>{{ item.description }}</p>
            </div>
          </div>
        </div>
      </VueSlickCarousel>
    </div>
  </div>
</template>

<script>
import VueSlickCarousel from "vue-slick-carousel";
// import CardTitle from "./CardTitle.vue";
import "vue-slick-carousel/dist/vue-slick-carousel.css";
import "vue-slick-carousel/dist/vue-slick-carousel-theme.css";

export default {
  name: "MyComponent",
  components: { VueSlickCarousel, 
    // CardTitle 
},

  data() {
    return {
      fakeData: [
        { id: 1, title: "Slide 1", description: "Description for slide 1" },
        { id: 2, title: "Slide 2", description: "Description for slide 2" },
        { id: 3, title: "Slide 3", description: "Description for slide 3" },
        { id: 4, title: "Slide 4", description: "Description for slide 4" },
        { id: 5, title: "Slide 5", description: "Description for slide 5" },
        { id: 6, title: "Slide 6", description: "Description for slide 6" },
        { id: 7, title: "Slide 7", description: "Description for slide 7" },
      ],
    };
  },
};
</script>

<style scoped>
.contenedor-padre {
  display: flex;
  justify-content: center;
  align-items: center;
  border: 3px solid blue;
}

.main {
  border: 2px solid red;
  width: 100%;
  height: 100%;
}

.carousel-item {
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.item-content {
  /**ACA MODIFICO LA ALTURA PARA MODIFICAR EL TAMAÑO DEL CAROUSEL*/
  width: 100%;
  height: 700px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #f0f0f0; /* Color de fondo para los divs */
  border: 1px solid #ccc; /* Borde para los divs */
}

.item-inner {
  text-align: center;
  padding: 20px;
}
</style>
