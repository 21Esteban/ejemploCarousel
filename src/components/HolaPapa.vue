<template>
  <div class="contenedor-padre">
    <div class="main">
      <VueSlickCarousel
        :arrows="false"
        :dots="true"
        :vertical="true"
        style="height: 100%"
      >
        <div  class="carousel-item" v-for="card in fakeData" :key="card.id">
          <div class="item-content">
            
              <CardTitle :title="card.title" :description="card.description" :width="card.width" :height="card.height"/>
            
          </div>
        </div>
        <!-- Aqui va el ultimo componente a renderizar (la grid) -->
        <div  class="carousel-item">
          <div class="item-content">
            
              <GridComponent :cards="fakeData"/>
            
          </div>
        </div>
      </VueSlickCarousel>
    </div>
  </div>
</template>

<script>
import VueSlickCarousel from "vue-slick-carousel";
import CardTitle from "./CardTitle.vue";
import GridComponent from './GridComponent.vue';
import "vue-slick-carousel/dist/vue-slick-carousel.css";
import "vue-slick-carousel/dist/vue-slick-carousel-theme.css";


export default {
  name: "MyComponent",
  components: { VueSlickCarousel, 
     CardTitle , GridComponent
},

  data() {
    return {
      fakeData: [
      { id: 1, title: "Card 1", description: "Description for card 1", width: "300px", height: "200px" },
        { id: 2, title: "Card 2", description: "Description for card 2", width: "350px", height: "620px" },
        { id: 3, title: "Card 3", description: "Description for card 3", width: "320px", height: "180px" },
        { id: 4, title: "Card 4", description: "Description for card 4", width: "280px", height: "250px" },
        { id: 5, title: "Card 5", description: "Description for card 5", width: "400px", height: "300px" },
        // { id: 6, title: "Card 6", description: "Description for card 6", width: "350px", height: "200px" },
        // { id: 7, title: "Card 7", description: "Description for card 7", width: "300px", height: "250px" }
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
  /**ACA MODIFICO LA ALTURA PARA MODIFICAR EL TAMAÑO DEL CAROUSEL-CONTENEDOR QUE TIENE UN ELEMENTO DEL SLIDER*/
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
