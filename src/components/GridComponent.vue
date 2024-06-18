<template>
  <div class="parent">
    <div class="div1">
      <CardTitle
        :title="cards[1].title"
        :description="cards[1].description"
        :width="calcularAncho(cards[1].width,120)"
        :height="cards[1].height"
      />
    </div>
    <div class="div2"><CardTitle
        :title="cards[2].title"
        :description="cards[2].description"
        :width="calcularAncho(cards[2].width,120)"
        :height="cards[2].height"
      /></div>
    <div class="div3">
        <div class="div2"><CardTitle
        :title="cards[3].title"
        :description="cards[3].description"
        :width="calcularAncho(cards[3].width,120)"
        :height="cards[3].height"
      /></div>
    </div>
  </div>
</template>

<script>
import CardTitle from "./CardTitle.vue";

export default {
  props: {
    cards: {
      type: Object,
      required: true,
    },
  },
  components: {
    CardTitle,
  },
  methods:{
    calcularAncho(ancho,restica){
        return ancho - restica;
    }
  }
};
</script>

<style>
.parent {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-template-rows: repeat(2, 1fr);
  grid-column-gap: 15px;
  grid-row-gap: 0px;
}

.div1 {
  grid-area: 1 / 1 / 6 / 2;
}
.div2 {
  grid-area: 1 / 2 / 2 / 3;
}
.div3 {
  grid-area: 2 / 2 / 3 / 3;
}
</style>
