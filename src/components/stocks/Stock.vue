<template>
  <div class="flex-container ">
    <div>
      <div class="card mb-3">
        <div class="card-body">
          <h3 class="card-title">
            {{ stock.name }}
          </h3>
          <p class="card-text">Price: {{ stock.price }}</p>
          <input
            v-model.number="quantity"
            :class="{ danger: insufficientFunds }"
            type="number"
            class="form-control"
            placeholder="Quantity"
          >
          <button
            class="btn btn-success mt-2"
            @click="buyStock"
            :disabled="insufficientFunds || quantity <= 0 || !Number.isInteger(quantity)"
          >
            {{ insufficientFunds ? 'Not Enough' : 'Buy' }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>


<style scoped>
.danger {
  border: 1px solid red;
}

.card {
  width: 18rem; /* Adjust as needed */
  margin: 1rem; /* Adjust as needed */
}
</style>

<script>
export default {
  //DONE: Set props equal to stock using array syntax
  props: ['stock'],
  data () {
    return {
      //DONE: Create data object called quantity and set it to 0
      quantity: 0
    }
  },
  computed: {
    //DONE: Create a computed function called funds
    //DONE: Have funds() return $store.getters.funds
    funds(){
      return this.$store.getters.funds;
    },
    //DONE: Create a computed function called insufficientFunds
    //DONE: Have insufficientFunds() return this.quantity * this.stock.price > this.funds
    insufficientFunds(){
      return (this.quantity * this.stock.price) > this.funds
    }
  },
  methods: {
    //DONE: Create buyStock method
    //DONE: Create const called order that holds an object
    //DONE: Set stockId: to this.stock.id
    //DONE: Set stockPrice: to this.stock.price
    //DONE: Set quantity: to this.quantity
    //DONE: Outside the data object $store.dispatch() passing 'buyStock' and order
    //DONE: Reset quantity to 0
    buyStock(){
      const order = {
        stockId: this.stock.id,
        stockPrice: this.stock.price,
        quantity: this.quantity
      }
      this.$store.dispatch('buyStock',order)
      this.quantity = 0
    }
  }
}
</script>