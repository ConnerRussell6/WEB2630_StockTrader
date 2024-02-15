<template>
  <div>
    <div v-if="stocks.length === 0" class="text-center">
      <p class="font">Purchase a stock to see your portfolio.</p>
    </div>
    <!--DONE: Load app-stock component-->
    <!--DONE: Loop through stock in stocks using v-for-->
    <!--DONE: Bind to stock using : and pass stock from the v-for-->
    <div v-if="stocks.length > 0">
      <h3>You have stocks!</h3>
      <p>Manage your portfolio.</p>
    </div>
    <app-Stock
      v-for="stock in stocks"
      :key="stock.id"
      :stock="stock"
    >
  </app-Stock>
  </div>
</template>

<style>
.font {
  font-size: 20px;
}
</style>

<script>
//DONE: Import mapGetters from vuex
import { mapGetters } from 'vuex'
//DONE: Import Stock from ./Stock.vue
import Stock from './Stock.vue'
export default {
  computed: {
    //DONE: Create ...mapGetters method
    //DONE: Call stocks: 'stockPortfolio'
    ...mapGetters({
      stocks: 'stockPortfolio',
    }),    
  },
  //DONE: Initialize Stock component and name it appStock
  components:{
    appStock: Stock
  }
}
</script>