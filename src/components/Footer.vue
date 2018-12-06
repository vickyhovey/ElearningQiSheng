<template>
  <Footer id="footer" class="font-small pt-4 mt-4">
    <b-container class="text-left">
      <b-row>
        <b-col sm="6" cols="6">
          <h5 id="title" class="title">{{ title }} <img id="logo" src="../assets/nettbutikk1-logo-2.png"></img></h5>
          <p>Here you can sign up to our newsletter!</p>
          <b-input-group id="signupButton">
            <b-form-input type="email" v-model="user.email"></b-form-input><button v-on:click="signUp" class="btn btn-info" type="button" name="button">SignUp</button>
            </b-input-group>
        </b-col>
        <b-col sm="6" lg="6" cols="6">
          <h5 class="title">Information</h5>
          <ul>
            <li class="list-unstyled"><a href="#!">Contact</a></li>
            <li class="list-unstyled"><a href="#!">FAQ</a></li>
            <li class="list-unstyled"><a href="#!">Brands</a></li>
            <li class="list-unstyled"><a href="#!">Privacy Policy</a></li>
          </ul>
        </b-col>
      </b-row>
    </b-container>
    <div class="footer-copyright text-center py-3">
      <b-container fluid>
        <a href="#"><font-awesome-icon id="icon" :icon="{ prefix: 'fab', iconName: 'twitter' }"/></a>
        <a href="#"><font-awesome-icon id="icon" :icon="{ prefix: 'fab', iconName: 'facebook' }"/></a>
        <a href="#"><font-awesome-icon id="icon" :icon="{ prefix: 'fab', iconName: 'snapchat-square' }"/></a>
        <a href="#"><font-awesome-icon id="icon" :icon="{ prefix: 'fab', iconName: 'instagram' }"/></a>
      </b-container>
    </div>
  </Footer>
</template>

<script>
export default {
  props: ["title"],
  data () {
    return {
      user: { name: "", email: "" }
    }
  },
  methods: {
    signUp: function(){
      if(this.user.email == "") return
      this.$emit("signUp", this.user);
    }
  }
}
</script>

<style scoped>
#footer{
  background-color: lightgrey;
}
#title{
  font-size: 30px;
  font-family: 'Lora', serif;
}
#logo{
  height: 60px;
}
#icon{
  font-size: 30px;
  margin: 30px 10px 0 10px;
}
a {
  color: inherit;
 }
 #signupButton{
   cursor: pointer;
 }
</style>
