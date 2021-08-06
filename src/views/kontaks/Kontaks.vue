<template>
  <div class="kontaks">
    <!--<img alt="Vue logo" src="../assets/logo.png"> -->
    <Slider />
    <hr class="my-3">
      <router-link class="btn btn-primary" to="/createkontaks">Add kontak</router-link>

      <Cardkontaks :kontaks="kontaks" />


  </div>
</template>
<script>
import axios from 'axios'
// @ is an alias to /src
import Slider from "@/components/Slider.vue";
import Cardkontaks from "@/components/Cardkontaks.vue";
import { ref, onMounted } from 'vue';
export default {
  name: "Kontaks",
  components: {
    Slider,
    Cardkontaks,
  },
  setup(){
    let kontaks = ref([])
    onMounted(() => {
      axios.get('http://127.0.0.1:8000/api/kontaks')
      .then(response => {
        kontaks.value = response.data.data
      })
      .catch(error => {
        console.log(error)
      })
    })
    function kontakDelete(id){
      axios.delete(`http://127.0.0.1:8000/api/kontaks/${id}`)
      .then(()=>{
        let z = this.kontaks.map(kontaks => kontaks.id).indexOf(id);
        this.kontaks.splice(z, 1)
      }).catch(error => {
        console.log(error)
      })
    }
      return {
      kontaks,
      kontakDelete
    }
  }
};
</script>