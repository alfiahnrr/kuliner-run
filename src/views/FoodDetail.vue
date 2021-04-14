<template>
  <div class="foodDetail">
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
              <li class="breadcrumb-item active" aria-current="page">Food Detail</li>
            </ol>
          </nav>
        </div>
      </div>

      <!-- Content -->
      <div class="row">
        <div class="col md-6">
          <img :src="product.gambar" class="card-img-top" alt="..." key="gambar" />
        </div>
        <div class="col md-6">
          <h2>
            <b>{{product.name}}</b>
          </h2>
          <hr />
          <h4>
            <b>Harga</b>
            Rp. {{product.harga}}
          </h4>
          <form v-on:submit.prevent mt-3>
            <div class="form-check">
              <input
                v-model="order.rasa"
                class="form-check-input"
                type="radio"
                name="exampleRadios"
                id="exampleRadios1"
                value="original"
                checked
              />
              <label class="form-check-label" for="exampleRadios1">Original</label>
            </div>
            <div class="form-check">
              <input
                v-model="order.rasa"
                class="form-check-input"
                type="radio"
                name="exampleRadios"
                id="exampleRadios2"
                value="sedang"
              />
              <label class="form-check-label" for="exampleRadios2">Sedang</label>
            </div>
            <div class="form-check">
              <input
                v-model="order.rasa"
                class="form-check-input"
                type="radio"
                name="exampleRadios"
                id="exampleRadios3"
                value="pedas"
              />
              <label class="form-check-label" for="exampleRadios3">Pedas</label>
            </div>
            <div class="form-check">
              <input
                v-model="order.rasa"
                class="form-check-input"
                type="radio"
                name="exampleRadios"
                id="exampleRadios4"
                value="extrapedas"
              />
              <label class="form-check-label" for="exampleRadios4">Extra Pedas</label>
            </div>
            <br />
            <div class="form-row align-items-center">
              <div class="col-auto my-1">
                Jumlah Pesanan
                <label
                  class="mr-sm-2 sr-only"
                  for="inlineFormCustomSelect"
                >Jumlah Pesanan</label>
                <select
                  class="custom-select mr-sm-2"
                  id="inlineFormCustomSelect"
                  v-model="order.jumlah_pesanan"
                >
                  <option value="1">1</option>
                  <option value="2">2</option>
                  <option value="3">3</option>
                  <option value="4">4</option>
                  <option value="5">Lainnya</option>
                </select>
              </div>
            </div>
            <div class="form-group">
              Keterangan
              <textarea
                v-model="order.keterangan"
                class="form-control"
                aria-label="With textarea"
                placeholder="Misal : tidak pakai sayur, dll."
              ></textarea>
            </div>
            <div class="submit-group">
              <button type="submit" class="btn btn-success" @click="pemesanan">Pesan</button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import axios from "axios";

export default {
  name: "FoodDetail",
  components: {
    Navbar,
  },

  data() {
    return {
      product: "",
      order: {
        jumlah_pesanan: "",
        keterangan: "",
        products: [],
        rasa: "",
      },
    };
  },

  methods: {
    setProduct(data) {
      this.product = data;
    },

    pemesanan() {
      if (this.order.jumlah_pesanan) {
        this.order.products.push(this.product);
        axios
          .post(
            "https://6049c7e1fb5dcc001796a80f.mockapi.io/api/v1/keranjang",
            this.order
          )
          .then(() => {
            this.$router.push({path: "/keranjang"})
            this.$toast.success("Pesanan ditambahkan!", {
              type: "success",
              position: "top-right",
              duration: 3000,
              dismissible: true,
            });
          })
          .catch((error) => console.log(error));
      } else {
          this.$toast.error("Isi jumlah yang ingin dipesan!", {
            type : 'error',
            position : 'top-right',
            duration : 3000,
            dismissible : true,
          });
      }
    },
  },

  mounted() {
    axios
      .get(
        "https://6049c7e1fb5dcc001796a80f.mockapi.io/api/v1/kuliner-run/" +
          this.$route.params.id
      )
      .then((response) => this.setProduct(response.data))
      .catch((error) => console.log(error));
  },
};
</script>

<style>
.form-control {
  width: 200px;
}
</style>