<template>
  <div class="container cardContainer">
    <div class="mt-3 tableRow ">
      <!-- <div class="col"> -->
        <CardDisplay
          v-for="card in cardNumber"
          :key="card"
          :cardNumber="cardNumber"
          :rowCol="rowCol">
        </CardDisplay> 
      <!-- </div> -->
    </div>
  </div>
</template>

<script>
import CardDisplay from "./CardDisplay.vue"

export default {
  name: "CardList",
  components: {
    CardDisplay,
  },
  props: {
    cardNumber: {
      type: Number,
    },
    rowCol: {
      type: Number,
    },
  },
  methods: {},
  computed: {},
};
</script>

<style scoped>
.tableRow{
  max-width:390px;
  margin: 0 auto;
}
.cardContainer{
  margin:0;
  padding:0
}
@media (max-width: 768px) { 
   .tableRow{
   margin: 0;
   padding: 0;
  }
}
</style>