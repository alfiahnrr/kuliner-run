<template>
  <div>
    <Navbar />
    <div class="container">
      <div class="row ml-1">
        <div class="col mt-3">
          <h2>
            Daftar
            <strong>Makanan</strong>
          </h2>
        </div>
      </div>

      <div class="row mt-3">
        <div class="col">
          <div class="input-group mb-3">
            <input
            v-model="search"
              type="text"
              class="form-control"
              placeholder="Cari makanan favorit anda"
              aria-label="Search"
              aria-describedby="basic-addon1"
              @keyup="searchFood"
            />
            <div class="input-group-prepend">
              <span class="input-group-text" id="basic-addon1">
                <b-icon-search to="/"></b-icon-search>
              </span>
            </div>
          </div>
        </div>
      </div>

      <div class="row mt-3">
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
import CardProduct from "@/components/CardProduct.vue";
import axios from "axios";

export default {
  name: "Foods",
  components: {
    Navbar,
    CardProduct,
  },

  data() {
    return {
      products: [],
      search: '',
    };
  },

  methods: {
    setProducts(data) {
      this.products = data;
    },

  searchFood() {
    axios
      .get("https://6049c7e1fb5dcc001796a80f.mockapi.io/api/v1/kuliner-run?search="+this.search)
      .then((response) => this.setProducts(response.data))
      .catch((error) => console.log("Gagal ! ", error));
  }
  },

  mounted() {
    axios
      .get("https://6049c7e1fb5dcc001796a80f.mockapi.io/api/v1/kuliner-run")
      .then((response) => this.setProducts(response.data))
      .catch((error) => console.log("Gagal ! ", error));
  },
};
</script>

<style>
</style>