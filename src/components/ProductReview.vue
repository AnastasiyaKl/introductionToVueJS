<template>
    <form class="review-form" @submit.prevent="onSubmit">
        <p v-if="errors.length">
            <b>Please correct the following error(s):</b>
            <ul>
                <li v-for="error in errors">
                    {{error}}
                </li>
            </ul>
        </p>

        <p><label for="name">Name:</label><input type="text" id="name" v-model="name"></p>
        <p><label for="review">Review:</label><textarea id="review" v-model="review"></textarea></p>
        <p>
            <label for="rating">Rating:</label>
            <select id="rating" v-model.number="rating">
                <option>5</option>
                <option>4</option>
                <option>3</option>
                <option>2</option>
                <option>1</option>
            </select>
        </p>
        <p>Would you reccoment this product?</p>
        <div>
            <input type="radio" name="question" id="q1" value="yes" v-model="question">Yes
            <input type="radio" name="question" id="q2" value="no"  v-model="question">No
        </div>
        <input type="submit" value="Submit">
    </form>
</template>

<script>
  export default {
    name: 'ProductReview',
    data(){
      return{
        name: null,
        review: null,
        rating: null,
        question: null,
        errors: []
      }
    },
    methods:{
      onSubmit(){
        if(this.name && this.review && this.rating){
          let product_review = {
            name: this.name,
            review: this.review,
            rating: this.rating,
            question: this.question
          }
          this.$emit('review-submitted', product_review)
          this.name = null
          this.review = null
          this.rating = null
          this.question = null
        }
        else{
          if(!this.name) this.errors.push("Name required.");
          if(!this.review) this.errors.push("Review required.");
          if(!this.rating) this.errors.push("Rating required.");
        }
      }
    }
  }
</script>

<style scoped>

</style>