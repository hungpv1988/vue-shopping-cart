<template>
    <div class="cart">
        <h2>Your Cart</h2>
        <ul>
            <li v-for="item in products" :key="item.id">
                    {{ item.title }} - {{ item.price }} x {{ item.quantity }}
            </li>
        </ul>
       
        <p>Total: 1000000 usd</p>
        <p><button>Checkout</button></p>
        <p>Checkout.</p>
    </div>
</template>

<script>
export default {
    name : 'ShoppingCart',
    
    data() {
        return {
             products: [
                        {id: 1, title: 'Washing machine', price: '10000', quantity: 5},
                        {id: 2, title: 'Car', price: '20000', quantity: 6},
                        {id: 3, title: 'Air plane', price: '30000', quantity: 10}
                      ]
        }
    }
}
</script>
