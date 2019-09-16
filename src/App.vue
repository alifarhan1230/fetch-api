<template>
  <div id="app" class="container">
    <p v-if="loading">Loading...</p>
    <div v-else>
      <h3 class="heading">Pembayaran</h3>
      <table class="table table-bordered">
        <thead>
          <tr>
            <th scope="col">Npwpd</th>
            <th scope="col">Nama WP</th>
            <th scope="col">Alamat</th>
            <th scope="col">no_transaksi</th>
            <th scope="col">tanggal Bayar</th>
            <th scope="col">Bulan</th>
            <th scope="col">Tahun</th>
            <th scope="col">Pendapatan</th>
            <th scope="col">pajak Terhutang</th>
            <th scope="col">Denda</th>
            <th scope="col">Total Bayar</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="bayar in pembayaran" v-bind:key="bayar.id">
            <td>{{ bayar.npwpd }}</td>
            <td>{{ bayar.penanggung_pajak}}</td>
            <td>{{ bayar.alamat }}</td>
            <td>{{ bayar.no_transaksi }}</td>
            <td>{{ bayar.tgl_pembayaran }}</td>
            <td>{{ bayar.bulan }}</td>
            <td>{{ bayar.tahun }}</td>
            <td>{{ bayar.pendapatan }}</td>
            <td>{{ bayar.pajak_terhutang }}</td>
            <td>{{ bayar.denda }}</td>
            <td>{{ bayar.total_bayar }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from "axios";
// const baseURl = "http://localhost:3000/api_phr/pembayaran";

export default {
  name: "app",
  data() {
    return {
      loading: false,
      pembayaran: []
    };
  },
  mounted() {
    this.loading = true;
    axios
      .get("http://localhost:3000/api_phr/pembayaran/search/3.000.087.03.05")
      .then(response => (this.pembayaran = response.data))
      .catch(error => console.log(error))
      .finally(() => (this.loading = false));
  }
};
</script>

<script>
import axios from "axios";
// const baseURl = "http://localhost:3000/api_phr/pembayaran";

export default {
  name: "app",
  data() {
    return {
      loading: false,
      pembayaran: []
    };
  },
  mounted() {
    this.loading = true;
    axios
      .post("http://localhost:3000/api_phr/pembayaran/create")
      .then(response => (this.pembayaran = {}))
      .catch(error => console.log(error))
      .finally(() => (this.loading = false));
  }
};
</script>



<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
