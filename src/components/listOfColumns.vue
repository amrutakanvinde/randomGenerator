<template>
  <div class="container">
    <div class="row">
      <displayComponent
        v-for="card in cardNumber"
        :key="card"
        :cardNumber="cardNumber"
        :rowCol="rowCol"
      ></displayComponent>
    </div>
  </div>
</template>

<script>
import displayComponent from "./displayComponent.vue";

export default {
  name: "listOfColumns",
  components: {
    displayComponent,
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
