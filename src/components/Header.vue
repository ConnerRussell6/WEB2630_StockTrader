<template>
  <nav class="navbar navbar-expand-lg bg-body-tertiary">
    <div class="container-fluid">
      <!-- Left side: Brand -->
      <router-link to="/" class="navbar-brand">Stock Trader</router-link>

      <!-- Right side: Nav Items -->
      <div class="justify-content-end" id="navbarSupportedContent">
        <ul class="navbar-nav ml-auto">
          <router-link to="/portfolio" tag="li" active-class="nav-item"><a class="nav-link active">Portfolio</a></router-link>
          <router-link to="/stocks" tag="li" class="nav-item active"><a class="nav-link active">Stocks</a></router-link>
          <li class="nav-item">
            <a href="#" class="nav-link" @click="endDay">End Day</a>
          </li>
          <li class="dropdown" @click="isDropdownOpen=!isDropdownOpen" :class="{ open: isDropdownOpen }">
            <a href="#" class="dropdown-toggle">Save & Load</a>
            <ul class="dropdown-menu" v-if="isDropdownOpen">
              <li><a href="#" @click="saveData">Save Data</a></li>
              <li><a href="#" @click="loadData">Load Data</a></li>
            </ul>
          </li>
          <li class="nav-item">
            <strong class="navbar-text">Funds: {{ funds | currency }}</strong>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>



<style>
.navbar-nav a {
  color: black;
}

.navbar-nav a:active {
  color: rgb(189, 35, 35);
}

.navbar-brand {
  color: black;
}

.navbar-nav a:hover {
      color: #60a6c7; /* Set your desired hover color */
    }

.dropdown {
  position: relative;
  display: inline-block;
  padding: 7.5px;
  text-decoration: none;
}

.dropdown-toggle {
  cursor: pointer;
  text-decoration: none;
}

.dropdown-menu {
  text-decoration: none;
  display: none;
  position: absolute;
  z-index: 1;
  background-color: #fff;
  box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
  padding: 10px;
  list-style: none;
}

.dropdown-menu a {
  text-decoration: none;
  text-decoration: none;
  color: #333;
  display: block;
  padding: 5px;
}

.dropdown-menu a:hover {
  background-color: #f0f0f0;
  text-decoration: none;
}

.open .dropdown-menu {
  text-decoration: none;
  display: block;
}
</style>

<script>
//ToDo: Import mapActions from vuex
import {mapActions} from 'vuex'

export default {
  data () {
    return {
      //ToDo: Create data object called isDropdownOpen and set it to false
      isDropdownOpen: false
    }
  },
  computed: {
    //ToDo: Create a computed function called funds
    //ToDo: Have funds() return this.$store.getters.funds
    funds() {
      return this.$store.getters.funds
    }
  },
  methods: {
    //ToDo: Create ...mapActions method
    //ToDo: Call randomizeStocks: 'randomizeStocks'
    //ToDo: Call fetchData: 'loadData'
    ...mapActions({
      randomizeStocks: 'randomizeStocks',
      fetchData: 'loadData'
    }),

    //ToDo: Create endDay method
    //ToDo: Call randomizeStocks()
    endDay () {
      this.randomizeStocks()
    },

    //ToDo: Create SaveData method
    //ToDo: Create const called data that holds an object
    //ToDo: Set funds: to the $store getters funds
    //ToDo: Set stockPortfolio: to the $store getters stockPortfolio
    //ToDo: Set stocks: to the $store getters stocks
    //ToDo: Outside the data object use $http, using .put pass 'data.json' and the data object
    saveData () {
      const data = {
        funds: this.$store.getters.funds, 
        stockPortfolio: this.$store.getters.stockPortfolio,
        stocks: this.$store.getters.stocks,
      }
      this.$http.put('data.json', data)
    },

    //ToDo: Create loadData method
    //ToDo: Call fetchData()
    loadData () {
      this.fetchData()
    }
  }
}
</script>