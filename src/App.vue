<template>
	<div id="app" class="d-flex mt-0 img-fondo">
		<NavBar @page="page = $event" />
		<div class="container">
			<div>
				<h1 class="title">
					Garden Sushi
				</h1>
			</div>
			<div v-if="page == 'login'">
				<VueForm class="col-12" />
			</div>
      <div v-if="page == 'home'" class="row m-0 relative">
				<span class="total-price bg-success py-2 px-4">
					TOTAL: $ {{ total }}
				</span>
        <div class="container">
          <div class="row">
            <div v-for="categoria in categorias" :key="categoria.id" class="col-md-6 pb-4">
              <div class="align-items-center">
                <h2 class="ps-4 mb-0">{{ categoria.name }}</h2>
              </div>
              <div class="row">
                <div v-for="product in categoria.products" :key="product.id" class="col-md-6 pb-4">
                  <ProductsCard :product="product" @buy="addItem($event)" :carrito="carrito"/>
                </div>
              </div>
            </div>
          </div>
        </div>
			</div>
		</div>
	</div>
</template>

<script>
import NavBar from "./components/NavBar.vue";
import VueForm from "./components/VueForm.vue";
import ProductsCard from "./components/ProductsCard.vue";
export default {
	name: "App",
	components: {
		ProductsCard,
		NavBar,
		VueForm,
	},
	data() {
		return {
			page: "login",
			carrito: [],
			categorias: [
				{
					id: 1,
					name: "Combos",
					products: [
						{id: 1,name: "Combo 10",price: 1200, imgUrl:"./assets/Combo_10"},
						{id: 2,name: "Combo 15",price: 1800, imgUrl:"./assets/Combo_15"},
						{id: 3,name: "Combo 20",price: 2200, imgUrl:"./assets/Combo_20"},
						{id: 4,name: "Combo 30",price: 3300, imgUrl:"./assets/Combo_30"},
					],
				},
				{
					id: 2,
					name: "Postres",
					products: [
						{id: 5,name: "Torta Oreo (p/compartir)",price: 100},
						{id: 6,name: "Torta Oreo (Individual)",price: 100},
						{id: 7,name: "Cheesecake",price: 100},
					],
				},
			],
		};
	},
	computed: {
		total() {
			let res = 0;
			this.carrito.forEach((item) => {
				res += item.product.price * item.count;
			});
			return res;
		},
	},
	methods: {
		addItem(item) {
			let itemExists = false
			this.carrito.forEach((listItem) => {
				if (listItem.product.id == item.product.id) {
					listItem.count += item.sum;
					itemExists = true
				}
			});
			if (!itemExists) {
				this.carrito.push({product:item.product,count:1});
			}
		},
	},
};
</script>

<style scoped>
.border-green {
  border-top: 2px solid #9fff31;
}
.total-price {
	border-radius: 48px;
	z-index: 99;
	color: #fff;
	font-weight: bold;
	font-size: 32px;
	position: fixed;
	bottom: 20px;
	right: 20px;
	width: fit-content;
}
.tent-logo {
  width: 100px;
  border-radius: 12px;
}
.img-fondo{
  background-image: url(./assets/logoBG2.svg);
}
.title{
    font-size: 50px;
    font-family:courgette;
    text-align: center;
    color: #48887A;
    padding: 10px 0 10px 0;
    font-weight: 600;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /*text-align: center;*/
  color: #2c3e50;
  margin-top: 60px;
}
</style>
