<template>
<div class="row">
    <div class="col mt-3" v-for="(history, index) in historys" :key="index">
<div class="card">
  <h5 class="card-header align-items-center d-flex justify-content-center">Pendidikan</h5>
  <div class="card-body">
    <p class="card-title align-items-center d-flex justify-content-center">{{history.sd}}</p>
    <p class="card-title align-items-center d-flex justify-content-center">{{history.smp}}</p>
     <p class="card-title align-items-center d-flex justify-content-center">{{history.sma}}</p>
      <p class="card-title align-items-center d-flex justify-content-center">{{history.perguruan_tinggi}}</p>

  </div>
  <div class="card-footer text-muted align-items-center d-flex justify-content-center">
    <router-link class="btn btn-primary" :to="{name:'Detailhistorys', params:{id:history.id}}">Detail</router-link>
  </div>
</div>
</div>
</div>
</template>

<script>
export default {
    props: ["historys"],
};
</script>
