<template>
    <div class="card text-center mt-4">
  <div class="card-header">
    Detail History
  </div>
  <div class="card-body">
    <h5 class="card-title">{{history.sd}}</h5>
    <p class="card-text">{{history.smp}}</p>
    <p class="card-text">{{history.sma}}</p>
    <p class="card-text">{{history.perguruan_tinggi}}</p>
    
  </div>
  <div class="card-footer">
    <router-link class="btn btn-success" :to="{name:'Edithistorys', params:{id:history.id}}">Edit</router-link>
        <button @click.prevent="historyDelete(history.id)" class="btn btn-danger">Delete</button>
  </div>
</div>
</template>

<script>
import { onMounted, ref } from 'vue';
import { useRouter, useRoute } from 'vue-router'
import axios from 'axios'
export default {
  setup() {
      let history = ref([]);
    const router = useRouter();
    const route = useRoute()
    onMounted(()=>{
      axios.get(`http://127.0.0.1:8000/api/historys/${route.params.id}`)
      .then(response => {
        console.log(response.data.data.nama);
        history.value = response.data.data;
        
      }).catch(error =>{
        console.log(error.response.data);
      });
    });
    function historyDelete(id){
      axios.delete(`http://127.0.0.1:8000/api/historys/${id}`)
      .then(()=>{
        router.go(-1);
      }).catch(error => {
        console.log(error)
      })
    }
    
    return {
      history,
      router, 
      historyDelete,
      route
    }
  },
}
</script>
