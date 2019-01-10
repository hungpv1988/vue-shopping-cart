<script>
    import Vue from 'vue';
    import Vuex   from 'vuex';

    Vue.use(Vuex);

    const saledProductIds = [2 ,3];
    const carts = [];
    export default (
        {
            state: {
                products: [{id: 1, title: 'Washing machine', price: '10000'},  {id: 2, title: 'Car', price: '20000'},{id: 3, title: 'Air plane', price: '30000'}]
            },

            getters: {
                saleProducts: state => {
                    return state.products.filter(item => saledProductIds.includes(item.id));
                }
            },

            mutations:{
                addToCart(state, productId, cartId){
                    var cart = carts.find(item => item.cardId === cartId);
                    if (!cart){
                        cart = {cardId: cartId, productId: productId, quantity: 1};
                        carts.push(cart);
                    }
                    else{
                        cart.quantity++;
                    }
                },

                showMessage(state, msg){
                    alert(msg);
                }
            },

            actions: {
                // try with dispatch    
                showMessage({dispatch}, msg) {
                    dispatch('showProductTitle', msg);
                },

                showProductTitle({commit}, msg ) {
                     commit('showMessage', msg);
                }
            }
        }
    )
</script>

