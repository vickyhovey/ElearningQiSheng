<template>
  <div>
    <b-navbar toggleable="md" type="dark" variant="primary" sticky="sticky">
    <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>
    <b-navbar-brand id="title" v-on:click="clearSearch">{{ title }}</b-navbar-brand>
    <b-collapse is-nav id="nav_collapse">
    <!-- logo -->
    <b-navbar-nav>
      <b-nav-item href="#"><img id="logo" src="../assets/nettbutikk1-logo-2.png"></img></b-nav-item>
    </b-navbar-nav>
    <!-- Right aligned nav items - Search-bar -->
    <b-navbar-nav class="ml-auto">
      <b-nav-form>
        <b-form-input size="sm" v-model="searchProduct" v-on:input="passInput(searchProduct)" class="mr-sm-2" type="text" placeholder="Search"/>
        <!-- <b-button size="sm" class="my-2 my-sm-0"><font-awesome-icon icon="search" /></b-button> -->
      </b-nav-form>
      <!-- Shopping chart -->
      <b-nav-form>
        <b-btn v-b-modal.modal1 size="sm" class="my-2 my-sm-0">
        <font-awesome-icon icon="shopping-cart" /></b-btn>
        <div>
          <!-- Modal Component -->
          <b-modal id="modal1" title="Cart">
            <p class="my-4">Products: {{ cart }} Total Price: {{ totalPrice }}</p>
            <b-button
            v-on:click="deleteCartContent(cart)"
            class="btn btn-danger">Delete cart content
            </b-button>
          </b-modal>
        </div>
      </b-nav-form>
      <b-navbar-nav>
        <b-nav-item>Items in cart: {{ cartNumber }} item(s)</b-nav-item>
      </b-navbar-nav>
    </b-navbar-nav>
    <!-- Price -->
    <b-navbar-nav>
      <b-nav-item href="#">Price: {{ totalPrice }} kr</b-nav-item>
    </b-navbar-nav>
    </b-collapse>
    </b-navbar>
  <!-- Navbar -->
  <b-nav justified tabs>
    <b-nav-item v-on:click="filterByCategory('Klær')">Klær</b-nav-item>
    <b-nav-item v-on:click="filterByCategory('Gaveideer')">Gaveideer</b-nav-item>
    <b-nav-item v-on:click="filterByCategory('Elektronikk')">Elektronikk</b-nav-item>
    <b-nav-item v-on:click="filterByCategory('Hobby')">Hobby</b-nav-item>
  </b-nav>
</div>
</template>

<script>
export default {
  props: ["title", "totalPrice", "cart", "cartNumber"],
  data () {
    return {
      searchProduct: ''
    }
  },
  // Emit functions to App-component
  methods: {
    deleteCartContent: function(cart){
      this.$emit("deleteCartContent", cart);
    },
    passInput: function(searchProduct){
      this.$emit("passInput", searchProduct);
    },
    filterByCategory: function(category){
      this.$emit("filterByCategory", category);
    },
    clearSearch: function(){
      this.$emit("clearSearch");
    }
  }
}
</script>

<style scoped>
#title{
  cursor: pointer;
}
.navbar-brand{
  font-size: 30px;
  font-family: 'Lora', serif;
}
#underTitle{
  text-align: center;
}
#logo{
  height: 60px;
}
.navbar{
  padding: 0 200px 0 200px;
}
.nav{
  padding: 0 200px 0 200px;
}
</style>
