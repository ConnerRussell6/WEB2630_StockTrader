<template>
    <div class="col">
        <div class="card mb-3">
            <div class="card-body">
                <h3 class="card-title">
                    {{ stock.name }}
                </h3>
                <p class="card-text">Price: {{ stock.price }} | Quantity: {{ stock.quantity }}</p>
            
            <input v-model.number="quantity" :class="{ danger: insufficientQuantity }" type="number" class="form-control"
                placeholder="Quantity">
            <button class="btn btn-success" @click="sellStock"
                :disabled="insufficientQuantity || quantity <= 0 || !Number.isInteger(quantity)">
                <!--ToDo: Display insufficientQuantity data object and add if using ? 'Not Enough' else 'Sell'-->
                {{ insufficientQuantity ? 'Not Enough' : 'Sell' }}
            </button>
        </div>
        </div>

    </div>
</template>

<style scoped>
    .danger {
        border: 1px solid red;
    }

    .card {
  width: 20rem; /* Adjust as needed */
  margin: 3rem; /* Adjust as needed */
}

</style>

<script>
    //DONE: Import mapActions from vuex
    import { mapActions } from 'vuex'
    export default {
        //DONE: Set props equal to stock using array syntax
        props: ['stock'],
        
        data() {
            return {
                //DONE: Create data object called quantity and set it to 0
                quantity: 0
            }
        },
        computed: {
            //DONE: Create a computed function called insufficientQuantity
                //DONE: Have insufficientQuantity() return this.quantity > this.stock.quantity
            insufficientQuantity(){
                return this.quantity > this.stock.quantity;
            }
        },
        methods: {
            //DONE: Create ...mapActions method
                //DONE: Call placeSellOrder: 'sellStock'
            ...mapActions({
                placeSellOrder: 'sellStock'
            }),
            // //DONE: Create sellStock method
            //     //DONE: Create const called order that holds an object
            //         //DONE: Set stockId: to this.stock.id
            //         //DONE: Set stockPrice: to this.stock.price
            //         //DONE: Set quantity: to this.quantity
            // //DONE: Outside the data object pass the data object order to placeSellOrder()
            // //DONE: Reset quantity to 0
            sellStock(){
                const order = {
                    stockId: this.stock.id,
                    stockPrice: this.stock.price,
                    quantity: this.quantity
                }
                this.placeSellOrder(order)
                this.quantity = 0
            }
        }
    }
</script>