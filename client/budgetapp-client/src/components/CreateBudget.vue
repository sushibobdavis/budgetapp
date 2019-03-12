<template>
  <div>
      <div class="budget-container">  
        <h3>Enter a name:</h3>
        <div>
          <input type="text" v-model="name">
        </div>
        <h3>Enter your income:</h3>
        <div v-for="income in incomes">
          <div>
            <input type="text" v-model="income.name" placeholder="Enter a name">
          </div>
          <div>
            <input type="number" v-model="income.amount" placeholder="Enter an amount">
          </div>
        </div>
        <span><button @click="addIncome">Add income</button></span>
        <span>Total income: {{totalIncome}}</span>
        <h3>Enter your expenses:</h3>
        <div v-for="expense in expenses">
          <div>
            <input type="text" v-model="expense.name" placeholder="Enter a name">
          </div>
          <div>
            <input type="number" v-model="expense.amount" placeholder="Enter an amount">
          </div>
        </div>
        <span><button @click="addExpense">Add expense</button></span>
        <span>Total expenses: {{totalExpenses}}</span>
      </div>
    </div>
</template>

<script>
export default {
  name: 'CreateBudget',
  data() {
    return {
      name: '',
      expenses: [{name: '', amount: 0}],
      incomes: [{name: '', amount: 0}],
    }
  },
  methods: {
    addExpense() {
      this.expenses.push({ name: '', amount: 0})
    },
    addIncome() {
      this.incomes.push({ name: '', amount: 0})
    }    
  },
  computed: {
      numberOfBudgetItems() {
          return this.expenses.length
      },
    alltheNames() {
      return this.expenses.map(function(x,y) { return x.name }).join(',')
    },
    totalExpenses() {
      return this.expenses.filter(x => !isNaN(Number(x.amount)))
              .map(function(x) { return { amount: parseFloat(x.amount) }})
              .reduce(function(x,y) { return x+y.amount }, 0)
    },
    totalIncome() {
      return this.incomes.filter(function(x) { return !isNaN(Number(x.amount)) })
              .map(function(x) { return { amount: parseFloat(x.amount) }})
              .reduce(function(x,y) { return x+y.amount }, 0)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

div.budget-container {
  float: left;
  padding: 30px;
}
div.budget-container > div div {
  width:250px;
  display: inline;
  padding: 30px;
}
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
