<template>
    <div class="card text-center mt-4">
  <div class="card-header">
    Detail pengalaman
  </div>
  <div class="card-body">
    <h5 class="card-title">{{pengalaman.kerja}}</h5>
    <p class="card-text">{{pengalaman.usaha}}</p>
  </div>
  <div class="card-footer">
    <router-link class="btn btn-success" :to="{kerja:'Editpengalamans', params:{id:pengalaman.id}}">Edit</router-link>
        <button @click.prevent="pengalamanDelete(pengalaman.id)" class="btn btn-danger">Delete</button>
  </div>
</div>
</template>

<script>
import { onMounted, ref } from 'vue';
import { useRouter, useRoute } from 'vue-router'
import axios from 'axios'
export default {
  setup() {
      let pengalaman = ref([]);
    const router = useRouter();
    const route = useRoute()
    onMounted(()=>{
      axios.get(`http://127.0.0.1:8000/api/pengalamans/${route.params.id}`)
      .then(response => {
        console.log(response.data.data.nama);
        pengalaman.value = response.data.data;
        
      }).catch(error =>{
        console.log(error.response.data);
      });
    });
    function pengalamanDelete(id){
      axios.delete(`http://127.0.0.1:8000/api/pengalamans/${id}`)
      .then(()=>{
        router.go(-1);
      }).catch(error => {
        console.log(error)
      })
    }
    
    return {
      pengalaman,
      router, 
      pengalamanDelete,
      route
    }
  },
}
</script>
