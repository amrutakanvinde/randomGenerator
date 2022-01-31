<template>
  <div class="container">
    <div class="row mt-3">
      <CardDisplay
        v-for="card in cardNumber"
        :key="card"
        :cardNumber="cardNumber"
        :rowCol="rowCol"
      ></CardDisplay>
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
