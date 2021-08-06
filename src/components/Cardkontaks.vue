<template>
<div class="row">
    <div class="col mt-3" v-for="(kontak, index) in kontaks" :key="index">
<div class="card">
  <h5 class="card-header align-items-center d-flex justify-content-center">Hubungi Saya</h5>
  <div class="card-body">
    <p class="card-text align-items-center d-flex justify-content-center">{{kontak.no_tlp}}</p>
    <p class="card-text align-items-center d-flex justify-content-center">{{kontak.email}}</p>
    <p class="card-text align-items-center d-flex justify-content-center">{{kontak.instagram}}</p>
    <p class="card-text align-items-center d-flex justify-content-center">{{kontak.facebook}}</p>
  </div>
  <div class="card-footer text-muted align-items-center d-flex justify-content-center">
    <router-link class="btn btn-primary" :to="{name:'Detailkontaks', params:{id:kontak.id}}">Detail</router-link>
  </div>
</div>
</div>
</div>
</template>

<script>
export default {
    props: ["kontaks"],
};
</script>
