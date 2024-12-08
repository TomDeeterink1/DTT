
<script>
import axios from 'axios';

export default {
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

<template>
  <div>
    <h1>Data from API:</h1>
    <li></li>
  </div>
</template>

<style>

</style>