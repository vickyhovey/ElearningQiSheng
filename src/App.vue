<template>
  <div>
    <app-header
    v-on:clearSearch="clearSearch"
    v-on:passInput="passInput($event)"
    v-bind:title="title"
    v-bind:underTitle="underTitle"
    v-bind:totalPrice="totalPrice"
    v-bind:cart="cart"
    v-bind:cartNumber="cartNumber"
    v-bind:productArray="productArray"
    v-on:deleteCartContent="deleteCartContent($event)"
    v-on:filterByCategory="filterByCategory($event)">
    </app-header>

    <app-sale
    v-on:goToPromotion="goToPromotion($event)">
    </app-sale>

    <app-products
    v-bind:filteredArray="filteredArray"
    v-on:filteredProducts="filteredProducts($event)"
    v-bind:productArray="productArray"
    v-bind:totalPrice="totalPrice"
    v-bind:cart="cart"
    v-on:updateTotalPrice="updatePrice($event)"
    v-on:deleteCartContent="deleteCartContent($event)"
    ></app-products>

    <app-footer
    v-bind:title="title"
    v-on:signUp="signUp"
    ></app-footer>
  </div>
</template>

<script>
import title from './components/Header.vue';
import products from './components/Page-content-product.vue';
import signup from './components/Footer.vue';
import sale from './components/Page-content-sale.vue';

export default {
  components: {
    'app-header': title,
    'app-products': products,
    'app-footer': signup,
    'app-sale': sale
  },
  data () {
    return {
      title: 'Letsgo!',
      underTitle: 'En nettbutikk som er nummer én',
      totalPrice: 0,
      searchTerm: '',
      filteredProductArray: [],
      cart: [],
      cartNumber: 0,
      productArray: [{title: "Støvsuger", price: 999, category: "Elektronikk", img: "https://images.unsplash.com/photo-1527515673510-8aa78ce21f9b?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=008bf9ac4d1216a5a6b8bd64ee0590d8&auto=format&fit=crop&w=967&q=80"},
                    {title: "Spillkonsoll", price: 799, category: "Hobby", img: "https://images.unsplash.com/photo-1516111143745-fbfc2ebd6352?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=741f5c9f322726bb28d328a56869b36f&auto=format&fit=crop&w=774&q=80"},
                    {title: "Kvalitetsregnejakke", price: 499, category: "Klær", img: "https://images.unsplash.com/photo-1531343676727-dc87ed9b9426?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=e1a396094ab1e991abdd1439c48a2d37&auto=format&fit=crop&w=634&q=80"},
                    {title: "Kamera", price: 1449, category: "Elektronikk", img: "https://images.unsplash.com/photo-1519638831568-d9897f54ed69?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=cd9235f85f87848efbdc2b3ff11963a8&auto=format&fit=crop&w=1350&q=80"},
                    {title: "Ullgenser", price: 379, category: "Klær", img: "https://images.unsplash.com/photo-1519076381129-b4234ae7e573?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=1a8a4714f12fb27eb5925dc8a83e0085&auto=format&fit=crop&w=660&q=80"},
                    {title: "Kaffetrakter", price: 399, category: "Gaveideer", img: "https://images.unsplash.com/photo-1530016143569-dc4a7c89173b?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=8a72dcc3fc968bd9eb757e519313e787&auto=format&fit=crop&w=634&q=80"}]
    }
  },
  methods: {
    // Update price and cart inventory number for each new product added
    updatePrice: function(product){
        this.cart.push(product.title);
        this.cartNumber = this.cart.length;
        this.totalPrice += product.price;
    },
    // Delete all content of cart
    deleteCartContent: function(cartContent){
      if (confirm("Do you really want to delete the content of your cart?") == true){
        this.cart = [];
        this.cartNumber = 0;
        this.totalPrice = 0;
      }
    },
    // Set searchTerm in state to the passed child argument searchProduct
    passInput: function(searchProduct){
      this.searchTerm = searchProduct;
    },
    // Filter products by pressing each category
    filterByCategory: function(category){
      return this.filteredProductArray = this.productArray.filter((product) => {
        return product.category.match(category);
      });
    },
    // Clear searched products and go back to initial product line
    clearSearch: function(){
      this.filteredProductArray = this.productArray;
      this.searchTerm = '';
    },
    // Alert on sign up
    signUp: function(user){
      alert(`Thank you for signing up ${user.name}. We have added ${user.email} to our mailing list!`);
    },
    // On click function on carousel elements
    goToPromotion: function(sale){
      return this.filteredProductArray = this.productArray.filter((product) => {
        if(sale == "newProducts"){
          return product.category == "Klær";
        }else if(sale == "deals"){
          return product.category == "Elektronikk";
        }else if(sale == "christmas"){
          return product.category == "Gaveideer";
        }
      });
    }
  },
  computed: {
    // Search input filter based on searchTerm
    filteredArray: function(){
      return this.filteredProductArray.filter((product) => {
        return product.title.toLowerCase().match(this.searchTerm.toLowerCase());
      });
    }
  },
    // Create copy of productArray so not to mutate origial
    created() {
      this.filteredProductArray = this.productArray;
    }
}
</script>

<style>

</style>
