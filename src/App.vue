<template>
  <div id="app" class="d-flex mt-0">
    <NavBar />
    <div class="container">
      <div class="row">
        <ProductsCards
          v-for="product in products"
          :key="product.id"
          :product="product"/>
      </div>


    </div>
  </div>
</template>

<script>

import NavBar from './components/NavBar.vue'
import ProductsCards from './components/ProductsCards.vue'

export default {
  name: 'App',
  components: {
    NavBar, ProductsCards
  },
  data(){
    return{
      products:[
        { id: 1, name: 'Combo 10', cantidad: 10, precio: 1200, img: "./img/Combo_10.jpg"},
        { id: 2, name: 'Combo 20', cantidad: 20, precio: 2200, img: "./img/Combo_20.jpg"},
        { id: 3, name: 'Combo 30', cantidad: 30, precio: 3200, img: "./img/Combo_30.jpg"}
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
