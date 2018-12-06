<template >
  <div class="container-fluid">
      <b-carousel id="carousel1"
                  style="text-shadow: 1px 1px 2px #333;"
                  controls
                  indicators
                  background="#ababab"
                  :interval="4000"
                  img-width="300"
                  img-height="200"
                  v-model="slide"
                  @sliding-start="onSlideStart"
                  @sliding-end="onSlideEnd"
                  >
  <div v-on:click="goToPromotion('newProducts')">
    <b-carousel-slide caption="Nyheter"
      id="firstImg"
      text="De fresheste nye produktene"
      img-src="https://images.unsplash.com/photo-1533025625706-f321868a1e6c?ixlib=rb-0.3.5&s=5231666a1078bbbb889742931391585d&auto=format&fit=crop&w=1350&q=80"
      img-width
      img-height
    ></b-carousel-slide>
  </div>

  <div v-on:click="goToPromotion('deals')">
    <b-carousel-slide caption="Ukas tilbud!"
      id="secondImg"
      text="Få med deg de elleville tilbudene"
      img-src="https://images.unsplash.com/photo-1526178613552-2b45c6c302f0?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=d3181a14477908c8b2929af6df8d056b&auto=format&fit=crop&w=1350&q=80"
      img-width
      img-height
    ></b-carousel-slide>
  </div>

  <div v-on:click="goToPromotion('christmas')">
    <b-carousel-slide caption="Julesalget er snart i gang!"
      id="thirdImg"
      text="Hvorfor ikke starte gavehandelen tidlig?"
      img-src="https://images.unsplash.com/photo-1513885535751-8b9238bd345a?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=afd6ee375c4fe6ef1e055cda436bb949&auto=format&fit=crop&w=1350&q=80"
      img-width
      img-height
    ></b-carousel-slide>
    </div>
  </b-carousel>
</div>
</template>


<script>
export default {

  data () {
    return {
      slide: 0,
      sliding: null
    }
  },
  methods: {
    onSlideStart (slide) {
      this.sliding = true
    },
    onSlideEnd (slide) {
      this.sliding = false
    },
    goToPromotion: function(sale){
      this.$emit("goToPromotion", sale);
    }
  }
}
</script>

<style scoped>
#carousel1{
  max-width: 1030px;
  margin: 0 auto 40px auto;
  cursor: pointer;
}
#firstImg{
  max-height: 400px;
}
#secondImg{
  max-height: 400px;
}
#thirdImg{
  max-height: 400px;
}

</style>
