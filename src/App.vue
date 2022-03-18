<template>
<div id="app">

    <header>
      <h1>{{website.name}}</h1>
      <button @click="showCheckout">{{this.cart.length}} Checkout </button>
       </header>
       <lesson-list @addLesson="addItem"></lesson-list>
       <checkout :cart="cart" @removeLesson="removeFromCart"></checkout>
  </div>
</template>

<script>

import lessonList from './components/lesson_list.vue';
import checkout from './components/Checkout_form.vue';

export default {
  name: 'App',
  components: {
    checkout,
    lessonList
  },
  data() {
    return {
      lessons: {}, 
       cart: [{}], 
      website: {
        name: "Courses",
      
      },
      
    }
  },
  methods: {
    
       addItem(lessonPass) {
        this.cart.push(lessonPass);
        lessonPass.space--;
        console.log(lessonPass._id);
      },
    removeFromCart(lessonRemove){
             console.log(this.cart.length)

        for(let i=0; i<this.cart.length;i++){
          if(this.cart[i]._id === lessonRemove._id){
            lessonRemove.space++;
            this.cart.splice(this.cart.indexOf(lessonRemove),1)
          }
        }

    },
    showCheckout() { this.website.showProduct = this.website.showProduct ? false : true;}}
    
  
};
</script>

<style>
#app {

  
}
</style>
