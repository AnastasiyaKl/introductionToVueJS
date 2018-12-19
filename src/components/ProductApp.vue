<template>
    <div>
        <div class="cart">
            <p>Cart({{ cart.length }})</p>
        </div>
        <Product @add-to-cart="updateCart" />
        <Product @add-to-cart="updateCart" />
    </div>

</template>

<script>
  import Product from './Product'

  export default {
    name: 'ProductApp',
    components: {
      Product
    },
    data(){
      return{
        cart: []
      }
    },
    methods:{
      updateCart(id){
        this.cart.push(id);
      }
    }
  }
</script>