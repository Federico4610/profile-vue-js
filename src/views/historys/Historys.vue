<template>
  <div class="historys">
    <!--<img alt="Vue logo" src="../assets/logo.png"> -->
    <Slider />
    <hr class="my-3">
      <router-link class="btn btn-primary" to="/createhistorys">Add history</router-link>

      <Cardhistorys :historys="historys" />


  </div>
</template>
<script>
import axios from 'axios'
// @ is an alias to /src
import Slider from "@/components/Slider.vue";
import Cardhistorys from "@/components/Cardhistorys.vue";
import { ref, onMounted } from 'vue';
export default {
  name: "Historys",
  components: {
    Slider,
    Cardhistorys,
  },
  setup(){
    let historys = ref([])
    onMounted(() => {
      axios.get('http://127.0.0.1:8000/api/historys')
      .then(response => {
        historys.value = response.data.data
      })
      .catch(error => {
        console.log(error)
      })
    })
    function historyDelete(id){
      axios.delete(`http://127.0.0.1:8000/api/historys/${id}`)
      .then(()=>{
        let z = this.historys.map(historys => historys.id).indexOf(id);
        this.historys.splice(z, 1)
      }).catch(error => {
        console.log(error)
      })
    }
      return {
      historys,
      historyDelete
    }
  }
};
</script>