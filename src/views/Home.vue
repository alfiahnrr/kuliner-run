<template>
  <div class="home">
    <Navbar />
    <div class="container">
      <Hero />
      <div class="row mt-4">
        <div class="col ml-3">
          <h2>
            <strong>best</strong> food.
          </h2>
        </div>
        <div class="col">
          <router-link to="/foods" class="btn btn-outline-success float-right">Lihat semua menu</router-link>
        </div>
      </div>
      <div class="row mb-3">
        <div class="col-md-3 mt-3" v-for="product in products" :key="product.id">
          <CardProduct :product="product" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Navbar from "@/components/Navbar.vue";
import Hero from "@/components/Hero.vue";
import CardProduct from "@/components/CardProduct.vue";
import axios from "axios";

export default {
  name: "Home",
  components: {
    Navbar,
    Hero,
    CardProduct,
  },

  data() {
    return {
      products: [],
    };
  },

  methods: {
    setProducts(data) {
      this.products = data;
    },
  },

  mounted() {
    axios
      .get("https://6049c7e1fb5dcc001796a80f.mockapi.io/api/v1/bestfoood")
      .then((response) => this.setProducts(response.data))
      .catch((error) => console.log("Gagal ! ", error));
  },
};
</script>
