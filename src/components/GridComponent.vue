<template>
  <div class="parent">
    <div class="div1">

    </div>
    <div class="div2">

    </div>
    <div class="div3">

    </div>
  </div>
</template>

<script>

props:{
    
}

export default {

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

.div1 { grid-area: 1 / 1 / 6 / 2; }
.div2 { grid-area: 1 / 2 / 2 / 3; }
.div3 { grid-area: 2 / 2 / 3 / 3; }
</style>
