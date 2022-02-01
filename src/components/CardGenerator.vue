<template>
  <div class="container divContainer">
    <h1 class="fw-bold text-start text-dark">Card Generator</h1>
    <nav class=" navbar-light bg-white shadow p-3 mb-5 bg-body rounded">
      <div class="container-fluid">
        <form class="row gy-2 gx-3 align-items-center" style="font-family:Hind; font-size:14px" @submit.prevent="onSubmit">
          <p v-if="errors.length">
            <b>Please correct the following error(s):</b>
            <ul>
              <li v-for="(error,index) in errors" :key="index">{{ error }}</li>
            </ul>
          </p>
          Generate
          <div class="col-auto divInput">
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
          <div class="col-auto divInput">
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
          <div class="d-grid d-md-block mb-2 col align-self-end">
            <button type="submit" class="btn btn-primary fw-bold" :disabled="!isCard" >Generate</button>
          </div>
        </form>
      </div>
    </nav>

    <CardList v-if="isSubmitted && cardNumber && rowCol" :cardNumber="cardNumber" :rowCol="rowCol"></CardList>

  </div>
</template>

<script>
import CardList from "./CardList.vue";

export default {
  name: "CardGenerator",
  components: {
    CardList,
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
        if (this.cardNumber > 5) {
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
      this.errors = [];
      if (this.cardNumber > 5 || this.cardNumber < 0) {
        this.errors.push("Number of cards have to be within the 1-5 range");
        this.cardNumber = 0;
      }
    },
    rowColInputChange() {
      this.errors = [];
      this.isSubmitted = false;
      if (this.rowCol > 5 || this.rowCol < 0) {
        this.errors.push(
          "Number of rows/columns have to be within the 1-5 range"
        );
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
.divInput {
  width: 100px;
}
/* table {
  border-width: 60%;
} */
.divContainer{
  max-width: 75%;
  background-color: #CCCCCC;
}
@media (max-width: 768px) { 
  .divContainer{
    max-width: 95%;
    padding:0;
  }
  .tableRow{
    justify-content: center;
  }
  .cardContainer{
    margin: 0;
    padding: 0;
  }
  .card-body{
    padding:0;
  }
}

h1{
  font-family: 'Roboto Slab', serif;
  font-size: 50px;
  /* font-weight:700; */

}
/* .displayTable{
  border-width: 9px;
} */
.btn{
  font-size:16px
}

</style>