<template>
    <div class="cart">
        <h2>Your Cart</h2>
        <ul>
            <li v-for="item in normalizedProductsInCart" :key="item.id">
                    {{ item.title }} - {{ item.price }} x {{ item.quantity }}
            </li>
        </ul>
       
        <p>Total: {{amoungOfMoney}}</p>
        <p><button>Checkout</button></p>
    </div>
</template>

<script>
import { mapGetters } from 'vuex';

export default {
    name : 'ShoppingCart',

computed: {
       normalizedProductsInCart() {
           var items = this.cartProducts.map((cartProd) => {
               var prod = this.allProducts.find(entry => entry.id == cartProd.id);
               if (!prod){
                   return null;
               }

                return {
                    id: cartProd.id,
                    title: prod.title,
                    price: prod.price,
                    quantity: cartProd.quantity
                };
           }, this) ;

           return items.filter(entry => entry != null);
       },

       amoungOfMoney(){
           var amount = 0;
           this.normalizedProductsInCart.forEach(element => {
               amount  += element.price * element.quantity;
           });

           return amount;
       },

        ...mapGetters(['cartProducts']),
        ...mapGetters('product', ['allProducts']),
    }
}
</script>
