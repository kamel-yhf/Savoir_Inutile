<template>
  <div class="container">
    <div>
      <h2 class="title">
        Un savoir inutile par jour !
      </h2>
      <br>
      <h1 class="subtitle">
        {{phrase}}
      </h1>
      <button class="button" @click="update">Un nouveau savoir</button>
    </div>
  </div>
</template>

<script>
import axios from "axios";
const api = 'https://uselessfacts.jsph.pl/random.json?language=en';

export default {
  data(){
    return{
      phrase: "",
    }
  },
  methods:{
    update(){
      axios.get(api).then(response => this.phrase = response.data.text);
    }
  },
  mounted(){
    axios.get(api).then(response => this.phrase = response.data.text);
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 50px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 35px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.button {
  background-color: #4CAF50;
  color: white;
  padding: 16px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  transition-duration: 0.4s;
  cursor: pointer;
}

</style>
