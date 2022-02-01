<template>
  <div class="card mx-2 divCard" >
    <div class="card-body">
      <!-- <div class="container-fluid"> -->
        <table class="table table-bordered displayTable rounded" style="">
          <tbody>
            <tr v-for="(arr, index) in twoDimensionalRandomArr" :key="index">
              <td v-for="(a, index) in arr" :key="index" class="border-dark bg-white " style="font-family: 'Roboto Slab';border-width:9px;font-size:40px; height:60px; width: 60px; font-weight:900; padding: 0">{{ a }}</td>
            </tr>
          </tbody>
        </table>
      <!-- </div> -->
    </div>
  </div>
</template>
<script>
export default {
  name: "CardDisplay",
  props: {
    cardNumber: {
      type: Number,
    },
    rowCol: {
      type: Number,
    },
  },

  data() {
    return {
      twoDimensionalRandomArr: [],
    };
  },
  methods: {
    onLoadLogic() {
      //creating a new array with random alphabets
      let arr = [];
      for (let i = 0; i < Math.pow(this.rowCol, 2); i++) {
        arr = this.randomGenerator(arr);
      }
      //Making the array a two dimensional one to make displaying easier
      this.twoDimensionalRandomArr = this.twoDimGenerator(arr);
    },
    twoDimGenerator(arr) {
      let returnArr = [];
      let counter = 0;
      if (arr.length === Math.pow(this.rowCol, 2)) {
        for (let i = 0; i < this.rowCol; i++) {
          let rowArr = [];
          for (let j = 0; j < this.rowCol; j++) {
            rowArr.push(arr[counter]);
            counter++;
          }
          returnArr.push(rowArr);
        }
      }
      return returnArr;
    },
    randomGenerator(arr) {
      let alphabetArr = ["A","B","C","D","E","F","G","H","I","J","K","L","M","N","O","P","R","S","T","U","V","W","X","Y","Z",
      ];
      let randomAlphabet =
        alphabetArr[Math.floor(Math.random() * alphabetArr.length)];
      if (!arr.includes(randomAlphabet)) {
        arr.push(randomAlphabet);
      } else {
        this.randomGenerator(arr);
      }
      return arr;
    },
  },
  computed: {},
  created() {
      this.onLoadLogic();
  }
};
</script>
