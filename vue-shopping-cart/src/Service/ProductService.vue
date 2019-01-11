
<script>

const products = [{id: 1, title: 'Washing machine', price: '10000'},  {id: 2, title: 'Car', price: '20000'},{id: 3, title: 'Air plane', price: '30000'}];
const stocks = [{id:1, productId: 1, quantity: 5}, {id:2, productId: 2, quantity: 3}, {id:3, productId: 3, quantity: 4}];

export default {
    get(){
        return products;
    },

    checkProductAvailableInStock(productId){
        var productInfo = stocks.find(item => item.productId === productId);
        return (!productInfo && productInfo.quantity > 0); 
    },

    deductProductOutOfStock(productId){
        if (!this.checkProductAvailableInStock(productId)){
            return false;
        }

         var productInfo = stocks.find(item => item.productId === productId);
         productInfo.quantity--;
         return true;
    },

    getStocks(){
        return stocks;
    }
}
</script>

