<template>
    <ul>
        <li v-for="item in products" :key="item.id">
            {{item.title}} - {{item.price}}
            <br>

            <button @click="showMsg(item.title)">Add to cart</button>
        </li>
    </ul>
</template>

<script>
import {  mapState, mapGetters, mapMutations, mapActions   } from 'vuex';

export default {
    name: 'ProductList',

    mounted: function(){
      //  alert(this.$store.state.products.length);
    },

    computed : {
        // for state, even if namespeace is false, we need to indicate module name that contains state we want
        ...mapState({
            products: state => state.product.products
         }),

        ...mapGetters([
            'saleProducts'
        ]),
        // products(){
        //     return this.$store.getters.saleProducts;
        // }
    },

    methods:{
        ...mapMutations ({
            show: 'showMessage',
            addToCart: 'addToCart'
        }),

        ...mapActions({
             showMsg: 'showMessage'
        })
    }
}
</script>
