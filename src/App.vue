<template>
  <div>
    <!--DONE: Load app-header-->
    <app-header></app-header>
    <div>
      <div class="marginB">
        <transition
          name="slide"
          mode="out-in"
        >
          <!--DONE: Load router-view-->
          <router-view></router-view>
        </transition>
      </div>
    </div>
  </div>
</template>

<script>
//DONE: Import Header Component
import Header from './components/Header.vue'
export default {
  //DONE: Initialize Header component and name it appHeader
  components: {
    appHeader: Header
  },
  //DONE: On page creation dispatch 'initStocks' to the vuex $store
  created(){
    this.$store.dispatch('initStocks');
  }
  
}
</script>

<style>
body {
  padding-top: 30px;
  background-color: whitesmoke;
  overflow: hidden;
  font-size: 20px;
}


.marginB {
  width: 80%;
  margin-left: 10%;
  padding-top: 2.5%;
}


/*ToDo: Create slide-in effect for enter-active*/
.slide-enter-active {
  animation: slide-in 1s ease-out forwards;
}
/*ToDo: Create slide-out effect for leave-active*/
.slide-leave-active {
  transition: opacity 0.5s ease;
  opacity: 0;
  animation: slide-in 0.5s ease-out forwards;
}

/*ToDo: Create Keyframes for slide-in, remember to include from and to*/
/*You can use any settings*/
@keyframes slide-in {
  0% {
    transform: translateX(-30px);
  }
  100% {
    transform: translateY(0);
  }
}

/*ToDo: Create Keyframes for slide-out, remember to include from and to*/
/*You can use any settings*/
@keyframes slide-out {
  0% {
    transform: translateY(0);
  }
  100% {
    transform: translateY(-30px);
  }
}
</style>

