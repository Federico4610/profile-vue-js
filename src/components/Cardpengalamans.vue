<template>
<div class="row">
    <div class="col mt-3" v-for="(pengalaman, index) in pengalamans" :key="index">
<div class="card">
  <h5 class="card-header align-items-center d-flex justify-content-center">Pengalaman Kerja|Usaha</h5>
  <div class="card-body">
    <p class="card-title align-items-center d-flex justify-content-center">{{pengalaman.kerja}}</p>
    <p class="card-title align-items-center d-flex justify-content-center">{{pengalaman.usaha}}</p>
    
  </div>
  <div class="card-footer text-muted align-items-center d-flex justify-content-center">
    <router-link class="btn btn-primary" :to="{name:'Detailpengalamans', params:{id:pengalaman.id}}">Detail</router-link>
  </div>
</div>
</div>
</div>
</template>

<script>
export default {
    props: ["pengalamans"],
};
</script>
