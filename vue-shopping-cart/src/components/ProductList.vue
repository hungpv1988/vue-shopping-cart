<template>
    <ul>
        <li v-for="item in allProducts" :key="item.id">
            {{item.title}} - {{item.price}}
            <br>

            <button :disabled="!item.quantity" @click="insertOrUpdateCart(item)">Add to cart</button>
        </li>
    </ul>
</template>

<script>
import {  mapGetters, mapMutations, mapActions   } from 'vuex';

export default {
    name: 'ProductList',

    mounted: function(){
      //  alert(this.$store.state.products.length);
    },

    computed : {
        // for state, even if namespeace is false, we need to indicate module name that contains state we want
        ...mapGetters('product', [
            'allProducts'
        ]),
    },

    methods:{
        ...mapMutations ({
            show: 'showMessage',
            addToCart: 'addToCart'
        }),

        ...mapActions({
             showMsg: 'showMessage',
             insertOrUpdateCart: 'insertOrUpdateCart'
        })
    }
}
</script>
