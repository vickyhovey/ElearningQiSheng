<template>
  <div class="container">
    <ul>
      <li v-for="product in filteredArray">
        <b-card v-bind:title="product.title"
        v-bind:img-src="product.img"
        img-alt="Image"
        img-top
        tag="article"
        style="max-width: 20rem;"
        class="mb-2">
        <p class="card-text">
          Pris: {{ product.price }}kr
        </p>
        <b-button
        v-on:click="updateTotalPrice(product)"
        variant="success">Add to cart</b-button>
      </b-card>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["filteredArray"],
  data () {
    return {

    }
  },
  methods: {
    updateTotalPrice: function(product){
      this.$emit("updateTotalPrice", product);
    }
  }
}
</script>

<style scoped>
img{
  height: 300px;
  width: 100%;
}
ul{
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
}
li{
  list-style-type: none;
  text-align: center;
     flex: 1 0 33%;
}
</style>
