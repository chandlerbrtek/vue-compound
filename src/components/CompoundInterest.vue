<template>
  <div class="compoundinterest">
      <input v-model="inital" placeholder="Initial Investment">
      <input v-model="contribution" placeholder="Monthly Contribution">
      <input v-model="years" placeholder="Length of Time in Years">
      <input v-model="annualinterest" placeholder="Annual Interest Rate">
      <select v-model="compoundrate">
        <option disabled value="">Please select one</option>
        <option value="1">Anually</option>
        <option value="2"> Semi-annually</option>
        <option value="12">Monthly</option>
        <option value="365">Daily</option>
     </select>

      <button v-on:click="calculateValue">Calculate</button>
      <input v-model="result" placeholder="Result" disabled>
  </div>
</template>

<script>
export default {
  name: 'CompoundInterest',
  data() {
    return {
        inital: 0,
        contribution: 0,
        years: 0,
        annualinterest: 0,
        result: 0,
        compoundrate: 0,
        contributions: [],
        values: [],
    }
  },
  methods: {
    calculateValue () {
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
