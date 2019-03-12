<template>
  <div>
      <div class="budget-container">        
        <div v-for="item in budgetItems">{{item.name}}
          <div>
            <input type="text" v-model="item.name" placeholder="Enter a name">
          </div>
          <div>
            <input type="text" v-model="item.value" placeholder="Enter a value">
          </div>
        </div>
      </div>
      <button @click="addBudgetItem">Add Item</button>
<span>Total spent: {{totalSpent}}</span>
      <span>You have created {{numberOfBudgetItems}} budget items {{alltheNames}}</span>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      budgetItems: []
    }
  },
  methods: {
    addBudgetItem() {
      this.budgetItems.push({ 'name': '', 'value': null})
      console.log(this.budgetItems)
    }
  },
  computed: {
      numberOfBudgetItems() {
          return this.budgetItems.length
      },
    alltheNames() {
      return this.budgetItems.map(function(x,y) { return x.name }).join(',')
    },
    totalSpent() {
      return this.budgetItems.filter(function(x) { return x.value }).reduce(function(x,y) { return x+y.value}, 0)
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
