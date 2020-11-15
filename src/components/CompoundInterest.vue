<template>
  <div class="compoundinterest">
      <input 
      v-model="inital" v-on:keyup="calculateValue" placeholder="Initial Investment ">
      <input v-model="contribution" v-on:keyup="calculateValue" placeholder="Monthly Contribution">
      <input v-model="years" v-on:keyup="calculateValue" placeholder="Length of Time in Years">
      <input v-model="annualinterest" v-on:keyup="calculateValue" placeholder="Annual Interest Rate">
      <select v-model="compoundrate" v-on:change="calculateValue">
        <option disabled value="">Please select one</option>
        <option value="1">Anually</option>
        <option value="2"> Semi-annually</option>
        <option value="12">Monthly</option>
        <option value="365">Daily</option>
     </select>
      <input v-model="result" placeholder="Result" disabled>
  </div>
</template>

<script>
export default {
  name: 'CompoundInterest',
  data() {
    return {
        inital: '',
        contribution: '',
        years: '',
        annualinterest: '',
        result: 0,
        compoundrate: '',
        contributions: [],
        values: [],
    }
  },
  methods: {
    calculateValue () {
      if (this.inital && this.contribution && this.years && this.annualinterest && this.compoundrate) {
        this.values = []
        this.contributions = []
        const annualContribution = this.contribution * 12
        const interestRate = 1 + (this.annualinterest / 100 / this.compoundrate)
      
        this.values.push(this.inital * 1);
        this.contributions.push(this.inital * 1);

        for (var i = 0; i < this.years; i++) {
          this.values.push(this.values[i] * interestRate + (annualContribution / this.compoundrate))
          this.contributions.push(this.contributions[i] + annualContribution);
          for (var j = 0; j < this.compoundrate - 1; j++) {
            this.values[i+1] = this.values[i+1] * interestRate + (annualContribution / this.compoundrate)
          }
        }
        this.result = this.values[this.years].toFixed(2)
      } else {
        this.result = 0
      }
    }
  }
}
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
