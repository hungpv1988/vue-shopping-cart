<script>
    import Vue from 'vue';
    import Vuex   from 'vuex';
    import product from './modules/product.vue';
    import cart from './modules/cart.vue';

    Vue.use(Vuex);

    export default new Vuex.Store(
        {
            modules:{
                product,
                cart
            }
        }
    )
</script>

