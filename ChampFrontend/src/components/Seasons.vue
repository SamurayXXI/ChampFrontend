<template>
  <div class="Seasons">
    <h1>Сезоны {{ id }}</h1>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Seasons',
  props: {
    id: Number
  },
  data() {
    return {
      champs: null
    };
  },
  mounted() {
    axios
      .get('http://localhost:8000/championships/', { 'headers': {"accept": "application/json"} })
      .then(response => (this.champs = response.data));
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
