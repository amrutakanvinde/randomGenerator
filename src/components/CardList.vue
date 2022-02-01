<template>
  <div class="container cardContainer">
    <div class="mt-3 tableRow ">
      <!-- <div class="container"> -->
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
