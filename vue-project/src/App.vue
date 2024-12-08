<template>
  <Header></Header>
  
  <router-view></router-view>
  
</template>
<script>
import Header from "./components/Header.vue";
import Home from "./components/Home.vue";

import axios from 'axios';
export default {
  components:{
    Header,
    Home
  },
  data() {
    return {
      data: null,
    };
  },
  mounted() {
    this.fetchData();
  },
  methods: {
    async fetchData() {
      try {
        const apiKey = import.meta.env.VITE_API_KEY;
        const response = await axios.get('https://api.intern.d-tt.nl/api/houses', {
          headers: {
               'X-Api-Key': apiKey,
          },
        });

        this.data = response.data;
      } catch (error) {
        console.error('Error fetching data:', error);
      }
    },
  },
};


</script>

<style>

</style>