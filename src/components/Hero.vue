<template>
  <div class="hero">
    <!--Dekstop--->
    <div class="md-none d-md-block">
      <div class="row">
        <div class="col-md-6">
          <div class="d-flex h-100">
            <div class="justify-content-center align-self-center ml-3">
              <h2>
                <strong>Delicious Menu,</strong>
                <br />Just In One Click.
              </h2>
              <p>Pilih makanan favoritmu disini tanpa repot, tanpa antri.</p>
              <router-link class="btn btn-lg btn-success" to="/foods">
                <b-icon class="mr-2" icon="circle-fill" animation="throb" font-scale="1.2">
                </b-icon>Pesan
              </router-link>
            </div>
          </div>
        </div>
        <div class="col-md-6">
          <img src="../assets/image/Hero.png" width="100%" />
        </div>
      </div>
    </div>

    <!--Mobile--->
    <!-- gambar masih dibawah, belum bisa diatas konten -->
    <div class="d-sm-block d-md-none">
      <div class="row-md-4">
        <div class="col-md-6 mb-2">
          <img src="../assets/image/Hero.png" width="100%" />
        </div>
        <div class="col-md-6">
          <div class="d-flex h-100">
            <div class="justify-content-center align-self-center ml-3">
              <h2>
                <strong>Delicious Menu,</strong>
                <br />Just In One Click.
              </h2>
              <p>Pilih makanan favoritmu disini tanpa repot, tanpa antri.</p>
              <button class="btn btn-lg btn-success">
                <b-icon icon="circle-fill" animation="throb" font-scale="1.3"></b-icon>Pesan
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>