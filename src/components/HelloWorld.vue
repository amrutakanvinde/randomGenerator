<template>
  <div class="container-fluid align-items-center">
    <h1>Card Generator</h1>
    <nav class=" navbar-light bg-light text-center">
      <div class="container-fluid">
        <form
          class="row gy-2 gx-3 align-items-center"
          @submit.prevent="onSubmit"
        >
        <p v-if="errors.length">
      <b>Please correct the following error(s):</b>
      <ul>
        <li v-for="(error,index) in errors" :key="index">{{ error }}</li>
      </ul>
    </p>
          Generate
          <div class="col-auto">
            <input
              type="number"
              class="form-control"
              id="cardNumber"
              placeholder="0"
              v-model.number="cardNumber"
              v-on:input="cardInputChange"
            />
          </div>
          random cards, each with
          <div class="col-auto">
            <input
              type="number"
              class="form-control"
              id="rowCol"
              v-model.number="rowCol"
              placeholder="0"
              v-on:input="rowColInputChange"
            />
          </div>
          rows/columns.

          <div class="d-grid d-md-block">
            <button type="submit" class="btn btn-primary" :disabled="!isCard" >Generate</button>
          </div>
        </form>
      </div>
    </nav>

    <listOfColumns v-if="isSubmitted && cardNumber && rowCol" :cardNumber="cardNumber" :rowCol="rowCol"></listOfColumns>

    
  </div>
</template>

<script>
import listOfColumns from "./listOfColumns.vue";

export default {
  name: "HelloWorld",
  components: {
    listOfColumns,
  },
  props: {
    msg: String,
  },
  data() {
    return {
      cardNumber: 0,
      rowCol: 0,
      isSubmitted: false,
      errors: [],
    };
  },
  methods: {
    onSubmit() {
      this.errors = [];
      this.isSubmitted = false;
      if (this.cardNumber > 0 && this.rowCol > 0) {
        if (this.cardNumber > 5 || this.cardNumber < 0) {
          this.errors.push("Number of cards have to be within the 1-5 range");
        } else if (this.rowCol > 5 || this.rowCol < 0) {
          this.errors.push(
            "Number of rows/columns have to be within the 1-5 range"
          );
        } else {
          this.isSubmitted = true;
        }
      }
    },
    cardInputChange() {
      this.isSubmitted = false;
      if (this.cardNumber > 5 || this.cardNumber < 0) {
        this.errors.push("Number of cards have to be within the 1-5 range");
        this.cardNumber = 0;
      }
    },
    rowColInputChange() {
      this.isSubmitted = false;
      if (this.rowCol > 5 || this.rowCol < 0) {
        this.errors.push("Number of rows/columns have to be within the 1-5 range");
        this.rowCol = 0;
      }
    },
  },
  computed: { 
    isCard() {
      return this.cardNumber && this.rowCol;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
