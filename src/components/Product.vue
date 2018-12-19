<template>
    <div>
        <div class="product">
            <div class="product-image">
                <!--<img src="@/assets/1.jpg" />-->
                <!--<img :src="require(`@/${image}`)" alt="">-->
                <img :src="image" />
            </div>

            <div class="product-info">
                <h1>{{ title }}</h1>
                <p v-if="inStock">In Stock</p>
                <p v-else>Out of Stock</p>
                <!--<a :href="link" target="_blank">More products like this</a>-->
                <div v-for="(variant, index) in variants"
                     :key="variant.variantID"
                     class="color-box"
                     :style="{backgroundColor: variant.variantColor}"
                     @mouseover="updateProduct(index)">
                </div>

                <div class="buttons">
                    <button v-on:click="addToCart" :disabled="!inStock" :class="{disabledButton: !inStock}">Add to Cart</button>
                    <button v-on:click="removeFromCart" v-if="cart>0">Remove from Cart</button>
                    <button v-on:click="emptyCart" v-if="cart>0">Empty Cart</button>
                </div>



            </div>
        </div>


        <div>
            <h2>Reviews</h2>
            <p v-if="!reviews.length">There are no reviews yet.</p>
            <ul>
                <li v-for="review in reviews">
                    <p>{{review.name}}</p>
                    <p>Rating: {{review.rating}}</p>
                    <p>{{review.review}}</p>
                </li>
            </ul>
        </div>

        <ProductReview @review-submitted="addReview"/>
    </div>
</template>


<script>
    import ProductReview from './ProductReview'
    export default {
    name: 'Product',
    components: { ProductReview },
    data(){
      return{
        brand: "Vue Mastery",
        product: "Socks",
        selectedVariant: 0,
        // image: "img/vmSocks-green.jpg",
        // image: "assets/vmSocks-green.jpg",
        variants: [
          {
            variantID: 1,
            variantColor: 'green',
            variantImg: "img/vmSocks-green.jpg",
            variantQuantity: 10
          },
          {
            variantID: 2,
            variantColor: 'blue',
            variantImg: "img/vmSocks-blue.jpg",
            variantQuantity: 1
          }
        ],
        reviews: [],

        link: "https://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=socks",

      }
    },

    methods: {
      updateProduct(index){
        this.selectedVariant = index
      },
      addToCart(){
        this.$emit('add-to-cart', this.variants[this.selectedVariant].variantID)
      },
      removeFromCart(){
        if(this.cart>0){
          this.cart--
        }
      },
      emptyCart(){
        this.cart=0
      },
      addReview(product_review){
        this.reviews.push(product_review)
      }
    },
    computed:{
      title(){
        return this.brand + ' ' + this.product
      },
      image(){
        return this.variants[this.selectedVariant].variantImg
      },

      inStock(){
        return this.variants[this.selectedVariant].variantQuantity
      }
    }
  }
</script>

<style scoped>

</style>