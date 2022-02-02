<template>
  <div class="container mainContainer">
    <h1 class="fw-bold text-start text-dark mx-3">Card Generator</h1>
    <nav class=" navbar-light bg-white shadow mb-5 bg-body rounded mx-3">
      <div class="container-fluid col-lg-auto">
        <form class="row gx-3 align-items-center" style="font-family:Hind; font-size:14px" @submit.prevent="onSubmit">
          <p v-if="errors.length">
            <b>Please correct the following error(s):</b>
            <ul>
              <li v-for="(error,index) in errors" :key="index">{{ error }}</li>
            </ul>
          </p>
          <div class="col-auto divInputText gy-1">Generate</div>
          <div class="col-auto divInput gy-1" style="padding-left: 20px;">
            <input
              type="number"
              class="form-control"
              id="cardNumber"
              placeholder=""
              v-model.number="cardNumber"
              v-on:input="cardInputChange"
            />
          </div>
          <div class="col-auto divInputText gy-1">random cards, </div>
          <div class = "inputCollection inputCollection row col-lg-auto align-items-center col-md-12 me-auto gy-lg-0 gy-sm-2">
            <div class="col-auto divInputText gy-1">each with</div>
            <div class="col-auto divInput gy-1">
              <input
                type="number"
                class="form-control"
                id="rowCol"
                v-model.number="rowCol"
                placeholder=""
                v-on:input="rowColInputChange"
              />
            </div>
            <div class="col-auto divInputText gy-1">rows/columns.</div>
          </div>
          <div class="btn-generate d-grid mb-2 col-lg-auto col-md-12 align-self-end gy-2">
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
.navbar-light{
  padding: 12px 20px;
}
.divInput, 
.divInputText, 
.row.inputCollection {
  padding-right: 0;
}
.divInput input{
  width: 56px;
  padding: 7px 13px 7px 13px;
 }
.divContainer{
  max-width: 75%;
  background-color: #CCCCCC;
}

@media (max-width: 768px) { 
  .divContainer{
    max-width: 95%;
    padding:0;
  }
  .mainContainer{
    margin: 0;
    padding: 0;
  }
}

h1{
  font-family: 'Roboto Slab', serif;
  font-size: 50px;

}
.btn{
  font-size:16px
}

</style>