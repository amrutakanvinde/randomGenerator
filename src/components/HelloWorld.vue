<template>
  <div class="container-fluid">
    <h1>Card Generator</h1>
    <nav class="navbar navbar-light bg-light">
      <div class="container-fluid">
        <form
          class="row gy-2 gx-3 align-items-center"
          @submit.prevent="onSubmit"
        >
          Generate
          <div class="col-auto">
            <input
              type="number"
              class="form-control"
              id="cardNumber"
              placeholder="0"
              v-model.number="cardNumber"
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
            />
          </div>
          rows/columns.

          <div class="d-grid d-md-block">
            <button type="submit" class="btn btn-primary" :disabled="!isCard" >Submit</button>
          </div>
        </form>
      </div>
    </nav>

    <listOfColumns v-if="isSubmitted" :cardNumber="cardNumber" :rowCol="rowCol"></listOfColumns>

    
  </div>
</template>

<script>
import listOfColumns from './listOfColumns.vue';

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
      cardNumber: null,
      twoDimensionalRandomArr: [],
      rowCol: null,
      isSubmitted: false
    };
  },
  methods: {
    onSubmit() {
      if (this.cardNumber > 0 && this.rowCol > 0) {
        this.isSubmitted = true;
      }
    },
    
  },
  computed:{
    isCard(){
      return this.cardNumber && this.rowCol
    },
  }
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
