<template>
  <div class="row">
    <div class="col mt-3" v-for="(profil, index) in profils" :key="index">
      <div class="card">
        <h5 class="card-header align-items-center d-flex justify-content-center">Data Diri</h5>
        <div class="card-body">
          <h5 class="card-title align-items-center d-flex justify-content-center">{{ profil.nama }}</h5>
          <p class="card-text align-items-center d-flex justify-content-center">{{ profil.ttl }}</p>
          <p class="card-text align-items-center d-flex justify-content-center">{{ profil.alamat }}</p>
          <p class="card-text align-items-center d-flex justify-content-center">{{ profil.jk }}</p>
        </div>
        <div class="card-footer text-muted d-flex justify-content-center">
          <router-link
            class="btn btn-primary"
            :to="{ name: 'Detailprofils', params: { id: profil.id } }"
            >Detail</router-link
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["profils"],
};
</script>
