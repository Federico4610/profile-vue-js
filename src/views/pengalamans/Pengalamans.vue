<template>
  <div class="pengalamans">
    <!--<img alt="Vue logo" src="../assets/logo.png"> -->
    <Slider />
    <hr class="my-3">
      <router-link class="btn btn-primary" to="/Createpengalamans">Add pengalaman</router-link>

      <Cardpengalamans :pengalamans="pengalamans" />


  </div>
</template>
<script>
import axios from 'axios'
// @ is an alias to /src
import Slider from "@/components/Slider.vue";
import Cardpengalamans from "@/components/Cardpengalamans.vue";
import { ref, onMounted } from 'vue';
export default {
  name: "Pengalamans",
  components: {
    Slider,
    Cardpengalamans,
  },
  setup(){
    let pengalamans = ref([])
    onMounted(() => {
      axios.get('http://127.0.0.1:8000/api/pengalamans')
      .then(response => {
        pengalamans.value = response.data.data
      })
      .catch(error => {
        console.log(error)
      })
    })
    function pengalamanDelete(id){
      axios.delete(`http://127.0.0.1:8000/api/pengalamans/${id}`)
      .then(()=>{
        let z = this.pengalamans.map(pengalamans => pengalamans.id).indexOf(id);
        this.pengalamans.splice(z, 1)
      }).catch(error => {
        console.log(error)
      })
    }
      return {
      pengalamans,
      pengalamanDelete
    }
  }
};
</script>