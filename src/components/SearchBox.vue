<template>
    <div class="search-box">
      <input
        type="text"
        class="search-bar"
        placeholder="Search..."
        v-model="query"
        @keypress="fetchWeather"
      />
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        query: '', 
      };
    },
    methods: {
      fetchWeather(e) {
        if (e.key === 'Enter') {
          this.$emit('search', this.query); 
        }
      },
    },
  };
  </script>
  