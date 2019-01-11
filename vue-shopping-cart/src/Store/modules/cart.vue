<script>
//import ProductService from '../../Service/ProductService.vue';
export default {
    state:{
        items : []
    },

    mutations: {
        insertOrUpdateCart(state, product){
            var prod = state.items.find(item => item.id == product.id);
            if (!prod){
                prod = {id : product.id, quantity: 1};
                state.items.push(prod);
            }
            else{
                prod.quantity++;
            }
            
            product.quantity--;
        }
    },

    getters:{
        cartProducts: state => {
            return state.items;
        }
    },

    actions:{
        insertOrUpdateCart( {commit}, product){
            if (product.quantity <=0){
                return;
            }

            commit('insertOrUpdateCart', product);
        }
    }

}
</script>
