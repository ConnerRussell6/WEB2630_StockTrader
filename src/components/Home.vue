<template>
  <div>
    <h1>Trade or View your Portfolio</h1>
    <p>You may Save & Load your Data</p>
    <p>Click on 'End Day' to begin a New Day!</p>
    <p>Your Funds:
      <!--DONE: Call funds computed function and pipe the currency filter that is created in main.js-->
      {{ funds | currency }}
    </p>
  </div>
</template>

<style>

</style>

<script>
export default {
  computed: {
    //DONE: Create a computed function called funds
    //DONE: Have funds() return this.$store.getters.funds
    funds(){
      return this.$store.getters.funds;
    }
    
  }
}
</script>