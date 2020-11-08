<template>
  <div class="compoundinterest">
      <input v-model="inital" placeholder="Initial Investment">
      <input v-model="contribution" placeholder="Monthly Contribution">
      <input v-model="years" placeholder="Length of Time in Years">
      <input v-model="annualinterest" placeholder="Annual Interest Rate">
      <button v-on:click="doStuff">Calculate</button>
      <input v-model="result" placeholder="Result">
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
        values: [],
    }
  },
  methods: {
    doStuff () {
        for (var i = 0; i < this.years; i++) {
            const interestRate = 1 + this.annualinterest / 100
            const annualContribution = this.contribution * 12

            if (i === 0) {
                this.values.push(this.inital * interestRate + annualContribution)
            } else {
                this.values.push(this.values[i-1] * interestRate + annualContribution)
            }
        }
      this.result = this.values[this.years - 1]
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
