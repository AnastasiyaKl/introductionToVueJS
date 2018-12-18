<template>
    <div class="product">
        <!--<div class="product-image" v-for="(image, index) in images" v-bind:key="index">-->
            <!--<img v-attr="'src:'image"/>-->
            <!--&lt;!&ndash;<p>{{image}}</p>&ndash;&gt;-->
        <!--</div>-->
        <div class="product-image">
            <img :src="image" />
        </div>

        <div class="product-info">
            <h1>{{ product }}</h1>
            <!--<p v-if="inStock">In Stock</p>
            <p v-else>Out of Stock</p>
            <a :href="link" target="_blank">More products like this</a>-->
            <div v-for="variant in variants" :key="variant.variantID">
                <p @mouseover="updateProduct(variant.variantImg)">{{variant.variantColor}}</p>
            </div>

            <div class="buttons">
                <button v-on:click="cart++">Add to Cart</button>
                <button v-if="cart>0" v-on:click="cart--">Remove from Cart</button>
                <button v-if="cart>0" v-on:click="cart=0">Empty Cart</button>
            </div>
            

            <div class="cart">
                <p>Cart({{cart}})</p>
            </div>
        </div>
    </div>
</template>

<script>
  export default {
    name: 'ProductApp',
    data: () => {
      return{
        product: "Socks",
        image: "img/vmSocks-green.jpg",
        // images: [
        //   "../assets/vmSocks-green.jpg",
        //   // '../assets/2.jpg',
        //   // '../assets/3.jpg'
        // ],
        variants: [
          {
            variantID: 1,
            variantColor: 'green',
            variantImg: "img/vmSocks-green.jpg"
          },
          {
            variantID: 2,
            variantColor: 'blue',
            variantImg: "img/vmSocks-blue.jpg"
          }
        ],

        cart: 0,
        link: "https://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=socks"
      }
    },

    methods: {
      updateProduct: function(variantImage){
        this.image = variantImage
      }
    },
  }
</script>

<style scoped>
    body {
        font-family: tahoma;
        color:#282828;
        margin: 0px;
    }

    .nav-bar {
        background: linear-gradient(-90deg, #84CF6A, #16C0B0);
        height: 60px;
        margin-bottom: 15px;
    }

    .product {
        display: flex;
        flex-flow: wrap;
        padding: 1rem;
    }

    img {
        border: 1px solid #d8d8d8;
        width: 70%;
        margin: 40px;
        box-shadow: 0px .5px 1px #d8d8d8;
    }

    .product-image {
        width: 80%;
    }

    .product-image,
    .product-info {
        margin-top: 10px;
        width: 50%;
    }

    .color-box {
        width: 40px;
        height: 40px;
        margin-top: 5px;
    }

    .cart {
        margin-right: 25px;
        float: right;
        border: 1px solid #d8d8d8;
        padding: 5px 20px;
    }
    
    .buttons{
        display: flex;
    }

    button {
        margin-top: 30px;
        border: none;
        background-color: #1E95EA;
        color: white;
        height: 40px;
        width: 100px;
        font-size: 14px;
    }

    .disabledButton {
        background-color: #d8d8d8;
    }

    .review-form {
        width: 400px;
        padding: 20px;
        margin: 40px;
        border: 1px solid #d8d8d8;
    }

    input {
        width: 100%;
        height: 25px;
        margin-bottom: 20px;
    }

    textarea {
        width: 100%;
        height: 60px;
    }

    .tab {
        margin-left: 20px;
        cursor: pointer;
    }

    .activeTab {
        color: #16C0B0;
        text-decoration: underline;
    }
</style>