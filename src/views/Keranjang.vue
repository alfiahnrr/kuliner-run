<template>
  <div class="keranjang">
    <Navbar />
    <div class="container">
      <!-- Breadcrumb -->
      <div class="row mt-3">
        <div class="col">
          <nav aria-label="breadcrumb">
            <ol class="breadcrumb">
              <li class="breadcrumb-item">
                <router-link to="/" class="text-dark">Home</router-link>
              </li>
              <li class="breadcrumb-item">
                <router-link to="/foods" class="text-dark">Foods</router-link>
              </li>
              <li class="breadcrumb-item">
                <router-link to="/foodDetail" class="text-dark">Food Detail</router-link>
              </li>
              <li class="breadcrumb-item active" aria-current="page">Food Order</li>
            </ol>
          </nav>
        </div>
      </div>

      <!-- Content -->
      <div class="col">
        <h2>
          Keranjang
          <strong>Saya</strong>
        </h2>
        <div class="table-responsive mt-3">
          <table class="table table-borderless">
            <thead>
              <tr>
                <th scope="col">#</th>
                <th scope="col">Gambar</th>
                <th scope="col">Makanan</th>
                <th scope="col">Keterangan</th>
                <th scope="col">Jumlah Pesanan</th>
                <th scope="col">Harga</th>
                <th scope="col">Total</th>
                <th scope="col">Hapus</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(keranjang,index) in keranjangs" :key="keranjang.id">
                <th>{{index+1}}</th>
                <td><img :src="keranjang.products.gambar" class="card-img-top" alt="..." key="gambar" width="250px"/></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import axios from 'axios';

export default {
  name: "Keranjang",
  components: {
    Navbar,
  },

  data() {
    return {
      keranjangs: [],
    };
  },
  methods: {
    setKeranjang(data) {
      this.keranjangs = data;
    },
  },

  mounted() {
    axios
      .get("https://6049c7e1fb5dcc001796a80f.mockapi.io/api/v1/keranjang")
      .then((response) => this.setKeranjang(response.data))
      .catch((error) => console.log(error));
  },
};
</script>
