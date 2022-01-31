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
    <!-- <div v-if="isSubmitted">
    <div v-for="card in cardNumber" :key="card" >
    {{card}}
      <displayComponent :twoDimensionalRandomArr="twoDimensionalRandomArr"></displayComponent>
    </div>
    </div> -->
    <listOfColumns v-if="isSubmitted" :cardNumber="cardNumber" :rowCol="rowCol"></listOfColumns>

    
  </div>
</template>

<script>
import listOfColumns from './listOfColumns.vue';
// import displayComponent from './displayComponent.vue';

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
      // let arr = [];
      if (this.cardNumber > 0 && this.rowCol > 0) {
        this.isSubmitted = true;
        // for (let i = 0; i < Math.pow(this.rowCol, 2); i++) {
        //   arr = this.randomGenerator(arr);
        // }
        // this.twoDimensionalRandomArr = this.twoDimGenerator(arr);

      // this.cardNumber = null;
      // this.rowCol = null
      }
    },
    // twoDimGenerator(arr) {
    //   let returnArr = [];
    //   let counter = 0;
    //   if (arr.length === Math.pow(this.rowCol, 2)) {
    //     for (let i = 0; i < this.rowCol; i++) {
    //       let rowArr = [];
    //       for (let j = 0; j < this.rowCol; j++) {
    //         rowArr.push(arr[counter]);
    //         counter++;
    //       }
    //       returnArr.push(rowArr);
    //     }
    //   }
    //   return returnArr;
    // },
    // randomGenerator(arr) {
    //   let alphabetArr = [
    //     "A",
    //     "B",
    //     "C",
    //     "D",
    //     "E",
    //     "F",
    //     "G",
    //     "H",
    //     "I",
    //     "J",
    //     "K",
    //     "L",
    //     "M",
    //     "N",
    //     "O",
    //     "P",
    //     "R",
    //     "S",
    //     "T",
    //     "U",
    //     "V",
    //     "W",
    //     "X",
    //     "Y",
    //     "Z",
    //   ];
    //   let randomAlphabet =
    //     alphabetArr[Math.floor(Math.random() * alphabetArr.length)];
    //   if (!arr.includes(randomAlphabet)) {
    //     arr.push(randomAlphabet);
    //   } else {
    //     this.randomGenerator(arr);
    //   }
    //   return arr;
    // },
  },
  computed:{
    isCard(){
      return this.cardNumber && this.rowCol
    },
    // isRow(){}
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
