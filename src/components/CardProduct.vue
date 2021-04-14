<template>
  <div class="card shadow card-product">
    <img
      :src="product.gambar"
      class="card-img-top"
      alt="..."
      key="gambar"
    />
    <div class="card-body">
      <h5 class="card-title">{{product.name}}</h5>
      <p class="card-text">{{product.deskripsi}}</p>
      <router-link class="btn btn-success" :to="'/foods/'+product.id">
        <b-icon-cart class="mr-2"></b-icon-cart>Pesan
      </router-link>
      <p class="price-text mt-2" style="float:right;">Rp. {{product.harga}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardProduct",
  props: ["product"],
};
</script>

<style>
</style>