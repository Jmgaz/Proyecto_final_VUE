<template>
  <!-- <div class="container pb-4">
    <div class="row">
      <div class="col-lg-4 col-md-6 pb-4">
        <div class="card ">
          <img src="../assets/Combo_10.jpg" class="card-img-top" alt="Combinado 10 piezas">
          <div class="card-body">
          <h5 class="card-title">{{product.name}}</h5>
          <p>${{product.price}}</p>
          <ShopButton :product="product" @buy="$emit('buy',$event)" :carrito="carrito"/>
          </div>
        </div>
      </div>
    </div>
  </div> -->
  <div class="card">
    <img class="card-img-top" src="../assets/Combo_10.jpg" alt="Card image">
    <div class="card-body">
      <h4 class="card-title">{{product.name}}</h4>
      <p class="card-text">${{product.price}}</p>
      <ShopButton :product="product" @buy="$emit('buy',$event)" :carrito="carrito"/>
    </div>
  </div>

</template>

<script>
import ShopButton from "./ShopButton";
export default {
	components: { ShopButton },
	props: {
		product: Object,
		carrito: Array,
	},
};
</script>

<style scoped>
.card {
  font-family: roboto, sans-serif;
  letter-spacing: 1px;
  font-weight: 600;
  color: #575757;
  background-color: #F1F1F180;
  width: 100px;
}
</style>
