<script>
    //const saledProductIds = [2 ,3];

export default (
        {
            namespaced: true,
            state: {
                products: [
                            {id: 1, title: 'Washing machine', price: '10000', quantity: 5},
                            {id: 2, title: 'Car', price: '20000', quantity: 3},
                            {id: 3, title: 'Air plane', price: '30000', quantity: 6}
                          ]
            },

            getters: {
                allProducts: state => {
                    return state.products;
                },
            },

            mutations:{
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

