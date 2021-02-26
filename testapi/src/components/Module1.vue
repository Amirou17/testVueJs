<template>
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2 pt-5">
      <div class="container" :key="index" v-for="(entreprise, index) in entreprise">
        <div class="jumbotron col mb-7">
          <h3>{{ entreprise.name }}</h3>
          <hr>
          <h5>Nombre d'étoiles : {{ entreprise.stars }}</h5>
          <h6>Adresse : {{ entreprise.address }}</h6>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  data(){
    const headers = { "Content-Type": 'application/x-www-form-urlencoded' }
    axios.defaults.headers.post["Content-Type"] ='application/x-www-form-urlencoded';
    const data = {
      grant_type: "client_credentials",
      scope:"PAR_labonneboite_503ca342c19ffb85d53afaf8bb335e5002769fb84eb7f6620ad8855bf325f7e7 api_labonneboitev1",
      client_secret: "f3f2775034b73a44052df949dc6273dab44bd5f70b2e2c498ed15bc7519f7967",
      client_id: "PAR_labonneboite_503ca342c19ffb85d53afaf8bb335e5002769fb84eb7f6620ad8855bf325f7e7",
    }
    const url = "https://entreprise.pole-emploi.fr/connexion/oauth2/access_token?realm=%2Fpartenaire"
    axios.post(url, data, headers).then(e => console.log(e))
    return{
      config : {
        headers: {
          'Authorization' : 'Bearer 90jLSkFE-yEQgNJvNoyJ-H5gejU'
        }
      },
      entreprise: null
    }
  },
  mounted() {
    axios
        .get('https://api.emploi-store.fr/partenaire/labonneboite/v1/company/?rome_codes=M1607&page=1&page_size=10&departments=75,13', this.config)
        .then((reponse) => {
          this.entreprise = reponse.data.companies;
          console.log(this.entreprise)
        }).catch((reason) => {console.log(reason)});
  }
}
</script>

<style scoped>

</style>