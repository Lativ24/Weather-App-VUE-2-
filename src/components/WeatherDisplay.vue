<template>
    <div class="weather-wrap" v-if="typeof weather.main != 'undefined'">
      <div class="location-box">
        <div class="location">{{ weather.name }}, {{ weather.sys.country }}</div>
        <div class="date">{{ dateBuilder() }}</div>
      </div>
      <div class="weather-box">
        <div class="temp">{{ Math.round(weather.main.temp) }}°C</div>
        <div class="weather">{{ weather.weather[0].main }}</div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      weather: Object,
    },
    methods: {
      dateBuilder() {
        let d = new Date();
        let months = ["Enero", "Febrero", "Marzo", "Abril", "Mayo", "Junio", "Julio", "Agosto", "Setiembre", "Octubre", "Noviembre", "Diciembre"];
        let days = ["Domingo", "Lunes", "Martes", "Miércoles", "Jueves", "Viernes", "Sábado"];
  
        let day = days[d.getDay()];
        let date = d.getDate();
        let month = months[d.getMonth()];
        let year = d.getFullYear();
        return `${day} ${date} ${month} ${year}`;
      },
    },
  };
  </script>
  